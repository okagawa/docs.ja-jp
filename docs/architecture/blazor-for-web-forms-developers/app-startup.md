---
title: アプリの起動
description: アプリのスタートアップロジックを定義する方法について説明します。
author: csharpfritz
ms.author: jefritz
ms.date: 11/20/2020
ms.openlocfilehash: d812079f84f67409334d07c4c10c5577446503be
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509703"
---
# <a name="app-startup"></a>アプリの起動

ASP.NET 向けに記述されたアプリケーションには、通常、 `global.asax.cs` `Application_Start` HTML レンダリングと .net 処理の両方でどのサービスを構成して使用できるようにするかを制御するイベントを定義するファイルがあります。 この章では、ASP.NET Core と Blazor Server との違いについて説明します。

## <a name="application_start-and-web-forms"></a>Application_Start と Web フォーム

既定の web フォーム `Application_Start` メソッドは、多くの構成タスクに対応するために、長年にわたって拡張されています。  Visual Studio 2019 の既定のテンプレートを使用した新しい web フォームプロジェクトに、次の構成ロジックが含まれるようになりました。

- `RouteConfig` -アプリケーションの URL ルーティング
- `BundleConfig` -CSS と JavaScript のバンドルと縮小

これらの各ファイルはフォルダーに格納され、 `App_Start` アプリケーションの開始時に1回だけ実行されます。  `RouteConfig` 既定のプロジェクトテンプレートでは、 `FriendlyUrlSettings` アプリケーションの url がファイル拡張子を省略できるように、web フォームのが追加され `.ASPX` ます。  既定のテンプレートには、ページに対して永続的な HTTP リダイレクトステータスコード (HTTP 301) を提供するディレクティブも含まれています。このディレクティブを `.ASPX` 使用すると、拡張子を省略したファイル名を使用して、フレンドリ URL に対して永続的な http リダイレクト状態コード

ASP.NET Core と Blazor を使用すると、これらのメソッドは単純化され、クラスに統合され `Startup` ます。また、一般的な web テクノロジを優先するようになります。

## <a name="blazor-server-startup-structure"></a>Blazor サーバーのスタートアップ構造

Blazor サーバーアプリケーションは ASP.NET Core 3.0 以降のバージョンの上に存在します。  ASP.NET Core web アプリケーションは、 `Startup.cs` アプリケーションのルートフォルダーにあるクラスのメソッドのペアによって構成されます。  スタートアップクラスの既定のコンテンツを以下に示します。

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

ASP.NET Core の他の部分と同様に、Startup クラスは依存関係の挿入の原則によって作成されます。  は、 `IConfiguration` 構成時に後でアクセスできるように、パブリックプロパティのコンストラクターと格納されに提供されます。

`ConfigureServices`ASP.NET Core で導入されたメソッドを使用すると、フレームワークの組み込み依存関係挿入コンテナー用にさまざまな ASP.NET Core フレームワークサービスを構成できます。  さまざまな `services.Add*` 方法により、認証、razor ページ、MVC コントローラーのルーティング、SignalR、Blazor などの機能を他の多くのユーザー間で利用できるようにするサービスが追加されます。  このメソッドは web フォームでは必要ありませんでした。 ASPX、.ASCX、.ASHX、ASMX の各ファイルの解析と処理は、web.config 構成ファイルの ASP.NET を参照することによって定義されています。  ASP.NET Core での依存関係の挿入の詳細については、 [オンラインドキュメント](/aspnet/core/fundamentals/dependency-injection)を参照してください。

`Configure`メソッドには、ASP.NET Core する HTTP パイプラインの概念が導入されています。  このメソッドでは、アプリケーションに送信されたすべての要求を処理する [ミドルウェア](middleware.md) を上から下に宣言します。 既定の構成では、これらの機能のほとんどが web フォーム構成ファイルに分散されており、参照しやすいように1か所にまとめられています。

は、ファイルに配置されたカスタムエラーページの構成ではなくなりましたが、 `web.config` アプリケーション環境にラベルが付いていない場合は常に表示されるように構成されてい `Development` ます。  さらに、既定では、メソッドの呼び出しによって、セキュリティで保護されたページを TLS で処理するように ASP.NET Core アプリケーションが構成されました `UseHttpsRedirection` 。

次に、予期しない構成方法がに一覧表示され `UseStaticFiles` ます。  ASP.NET Core では、静的ファイル (JavaScript、CSS、イメージファイルなど) に対する要求のサポートを明示的に有効にする必要があります。また、既定では、アプリの *wwwroot* フォルダー内のファイルのみがパブリックにアドレス指定できます。

次の行は、web フォームから構成オプションの1つをレプリケートする最初の行 `UseRouting` です。  このメソッドは、パイプラインに ASP.NET Core ルーターを追加します。これは、ここで構成することも、ルーティングを検討できる個々のファイルで構成することもできます。  ルーティング構成の詳細については、 [「ルーティング」セクション](pages-routing-layouts.md)を参照してください。

このメソッドの最後のステートメントは、ASP.NET Core がリッスンしているエンドポイントを定義します。  これらのルートは、web サーバー上でアクセスできる web アクセス可能な場所であり、.NET によって処理され、返されるコンテンツを受信します。  最初のエントリは、 `MapBlazorHub` Blazor コンポーネントの状態とレンダリングが処理されるサーバーへのリアルタイムおよび永続的な接続を提供するために SignalR hub を構成します。  `MapFallbackToPage`メソッド呼び出しは、Blazor アプリケーションを開始するページの web アクセス可能な場所を示します。また、クライアント側からのディープリンク要求を処理するようにアプリケーションを構成します。  この機能は、ブラウザーを開いて、既定のプロジェクトテンプレートなど、アプリケーションの Blazor によって処理されたルートに直接移動した場合に機能します `/counter` 。 要求は、 *_Host* Blazor のページによって処理されます。このページでは、その後、ルーターが実行され、カウンターページがレンダリングされます。

## <a name="upgrading-the-bundleconfig-process"></a>BundleConfig プロセスのアップグレード

CSS スタイルシートや JavaScript ファイルなどのアセットをバンドルするテクノロジは大幅に進化しており、これらのリソースを管理するためのツールと手法が急速に進化しています。  このためには、Grunt/Gulp/WebPack などのノードコマンドラインツールを使用して、静的なアセットをパッケージ化することをお勧めします。

Grunt、Gulp、および WebPack のコマンドラインツールとそれに関連付けられている構成をアプリケーションに追加できます。 ASP.NET Core は、アプリケーションのビルドプロセス中にこれらのファイルを自動的に無視します。  呼び出しを追加して、タスクを実行することができます。そのためには、次のような構文を使用してプロジェクトファイル内にを追加します。これにより、 `Target` gulp スクリプトと `min` そのスクリプト内でターゲットがトリガーされます。

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

CSS ファイルと JavaScript ファイルを管理するための両方の方法の詳細については、 [ASP.NET Core のドキュメントでバンドルと、静的なアセット](/aspnet/core/client-side/bundling-and-minification) の縮小に関するドキュメントを参照してください。

>[!div class="step-by-step"]
>[前へ](project-structure.md)
>[次へ](components.md)
