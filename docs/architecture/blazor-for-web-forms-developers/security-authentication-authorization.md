---
title: 'セキュリティ: ASP.NET Web フォームおよびでの認証と承認 Blazor'
description: ASP.NET Web フォームおよびで認証と承認を処理する方法について説明し Blazor ます。
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 0344960237a5d9da61eb0d85987c44e136f1be48
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509846"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a>セキュリティ:ASP.NET Web Forms および Blazor  での認証と承認

ASP.NET の Web フォームアプリケーションからに移行する Blazor 場合、アプリケーションで認証が構成されていることを前提として、ほとんどの場合、認証と承認の実行方法を更新する必要があります。 この章では、ASP.NET Web フォームユニバーサルプロバイダーモデル (メンバーシップ、ロール、およびユーザープロファイルの場合) から移行する方法と、アプリから ASP.NET Core Id を使用する方法について説明し Blazor ます。 この章では、大まかな手順と考慮事項について説明しますが、詳細な手順とスクリプトについては、参照されているドキュメントを参照してください。

## <a name="aspnet-universal-providers"></a>ASP.NET ユニバーサルプロバイダー

ASP.NET 2.0 以降、ASP.NET Web Forms platform は、メンバーシップなどのさまざまな機能のプロバイダーモデルをサポートしています。 ユニバーサルメンバーシッププロバイダーは、オプションのロールプロバイダーと共に、一般的に ASP.NET Web フォームアプリケーションと共に展開されます。 現在も引き続き正常に機能する認証と承認を管理するための、堅牢で安全な方法を提供します。 これらのユニバーサルプロバイダーの最新のオファリングは、NuGet パッケージである、 [Microsoft](https://www.nuget.org/packages/Microsoft.AspNet.Providers)で提供されています。

ユニバーサルプロバイダーは、、、、などのテーブルを含む SQL データベーススキーマを操作し `aspnet_Applications` `aspnet_Membership` `aspnet_Roles` `aspnet_Users` ます。 [aspnet_regsql.exe コマンド](/previous-versions/ms229862(v=vs.140))を実行して構成すると、基になるデータを操作するために必要なすべてのクエリとコマンドを提供するテーブルとストアドプロシージャがプロバイダーによってインストールされます。 データベーススキーマとこれらのストアドプロシージャは、新しい ASP.NET Identity および ASP.NET Core Id システムと互換性がないため、既存のデータを新しいシステムに移行する必要があります。 図1は、ユニバーサルプロバイダー用に構成されたテーブルスキーマの例を示しています。

![ユニバーサルプロバイダースキーマ](./media/security/membership-tables.png)

ユニバーサルプロバイダーは、ユーザー、メンバーシップ、ロール、およびプロファイルを処理します。 ユーザーにはグローバル一意識別子が割り当てられ、ユーザー Id やユーザー名などの基本情報がテーブルに格納されます。 `aspnet_Users` パスワード、パスワード形式、パスワード salt、ロックアウトカウンター、詳細などの認証情報は、テーブルに格納されます。 `aspnet_Membership` ロールは、名前と一意の識別子の単純なもので構成され、アソシエーションテーブルを介してユーザーに割り当てられ `aspnet_UsersInRoles` 、多対多のリレーションシップを提供します。

既存のシステムがメンバーシップに加えてロールを使用している場合は、ユーザーアカウント、関連付けられているパスワード、ロール、およびロールメンバーシップを ASP.NET Core Id に移行する必要があります。 また、通常は、if ステートメントを使用して、宣言型のフィルター、属性、またはタグヘルパーを利用することで、現在ロールチェックを実行しているコードを更新する必要があります。 移行に関する考慮事項の詳細については、この章の最後を参照してください。

### <a name="authorization-configuration-in-web-forms"></a>Web フォームでの承認構成

ASP.NET Web フォームアプリケーションで特定のページへの承認されたアクセスを構成するには、通常、匿名ユーザーが特定のページまたはフォルダーにアクセスできないように指定します。 この構成は、web.config ファイルで行います。

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

構成セクションでは、 `authentication` アプリケーションのフォーム認証を設定します。 セクションは、 `authorization` アプリケーション全体の匿名ユーザーを許可しないために使用されます。 ただし、場所ごとにより詳細な承認規則を提供したり、ロールベースの承認チェックを適用したりすることができます。

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

上記の構成を最初の構成と組み合わせると、匿名ユーザーがログインページにアクセスできるようになり、認証されていないユーザーに対するサイト全体の制限が上書きされます。

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

上記の構成を他の構成と組み合わせて使用すると、 `/admin` フォルダーとその中のすべてのリソースへのアクセスが "Administrators" ロールのメンバーに制限されます。 この制限は、フォルダールート内に別のファイルを配置することでも適用でき `web.config` `/admin` ます。

### <a name="authorization-code-in-web-forms"></a>Web フォームでの認証コード

を使用してアクセスを構成するだけでなく `web.config` 、Web フォームアプリケーションのアクセスと動作をプログラムで構成することもできます。 たとえば、特定の操作を実行する機能を制限したり、ユーザーのロールに基づいて特定のデータを表示したりすることができます。

このコードは、コードビハインドロジックとページ自体の両方で使用できます。

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

ユーザーロールのメンバーシップを確認するだけでなく、認証されているかどうかを判断することもできます (ただし、上記の場所ベースの構成を使用することをお勧めします)。 このアプローチの例を次に示します。

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

上のコードでは、ロールベースのアクセス制御 (RBAC) を使用して、ページの特定の要素 (など) が `SecretPanel` 現在のユーザーのロールに基づいて表示されるかどうかを判断します。

通常、ASP.NET Web フォームアプリケーションは、ファイル内のセキュリティ `web.config` を構成し、 `.aspx` ページとその関連分離コードファイルに必要なチェックを追加し `.aspx.cs` ます。 ほとんどのアプリケーションは、多くの場合、追加の役割プロバイダーを使用して、ユニバーサルメンバーシッププロバイダーを利用します。

## <a name="aspnet-core-identity"></a>ASP.NET Core ID

認証と承認を行っていても、ASP.NET Core Id では、ユニバーサルプロバイダーと比較して、異なる抽象化と仮定を使用します。 たとえば、新しい Id モデルはサードパーティの認証をサポートしているため、ユーザーはソーシャルメディアアカウントまたは他の信頼された認証プロバイダーを使用して認証を行うことができます。 ASP.NET Core Id は、ログイン、ログアウト、登録など、一般的に必要なページの UI をサポートします。 データアクセスには EF Core を利用し、EF Core の移行を使用して、データモデルをサポートするために必要なスキーマを生成します。 [ASP.NET Core での id](/aspnet/core/security/authentication/identity)の概要では、ASP.NET Core id に含まれるものの概要と、その使用方法について説明します。 アプリケーションとそのデータベースに ASP.NET Core Id をまだ設定していない場合は、開始するのに役立ちます。

### <a name="roles-claims-and-policies"></a>役割、要求、およびポリシー

ユニバーサルプロバイダーと ASP.NET Core Id の両方で、ロールの概念がサポートされています。 ユーザーのロールを作成し、ユーザーをロールに割り当てることができます。 ユーザーは任意の数のロールに属することができ、承認実装の一部としてロールのメンバーシップを確認できます。

ロールに加えて、ASP.NET Core id では、信頼性情報とポリシーの概念がサポートされています。 ロールは、そのロールのユーザーがアクセスできる必要がある一連のリソースに特に対応する必要がありますが、要求は単にユーザーの id の一部になります。 クレームは、サブジェクトの内容を表す名前と値のペアであり、サブジェクトが実行できる内容ではありません。

ユーザーの要求を直接検査し、ユーザーにリソースへのアクセス権を付与する必要があるかどうかを、これらの値に基づいて判断することができます。 ただし、多くの場合、このようなチェックは繰り返し、システム全体にわたって分散されます。 より優れたアプローチは、 *ポリシー* を定義することです。

承認ポリシーは、1つまたは複数の要件で構成されます。 ポリシーは、のメソッドで承認サービス構成の一部として登録され `ConfigureServices` `Startup.cs` ます。 たとえば、次のコードスニペットでは、"Can" という名前のポリシーを構成しています。このポリシーでは、ユーザーが "カナダ" の値を持つ国の要求を持っている必要があります。

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

[カスタムポリシーの作成方法の詳細については、ドキュメントを参照して](/aspnet/core/security/authorization/policies)ください。

ポリシーまたはロールを使用しているかどうかにかかわらず、アプリケーションの特定のページで、 Blazor 属性を持つロールまたはポリシーが `[Authorize]` ディレクティブで適用される必要があることを指定でき `@attribute` ます。

ロールが必要:

```csharp
@attribute [Authorize(Roles ="administrators")]
```

ポリシーが満たされている必要があります。

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

コード内のユーザーの認証状態、ロール、または要求へのアクセスが必要な場合、この機能を実現するには主に2つの方法があります。 1つ目は、認証状態をカスケード型パラメーターとして受け取ることです。 2つ目は、挿入されたを使用して状態にアクセスすることです `AuthenticationStateProvider` 。 これらの各方法の詳細については、 [ Blazor セキュリティのドキュメント](/aspnet/core/blazor/security/)を参照してください。

次のコードは、をカスケード型 `AuthenticationState` パラメーターとして受け取る方法を示しています。

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

このパラメーターを使用すると、次のコードを使用してユーザーを取得できます。

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

次のコードは、を挿入する方法を示してい `AuthenticationStateProvider` ます。

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

プロバイダーを配置すると、次のコードを使用してユーザーにアクセスできます。

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

**注:**`AuthorizeView`この章の後半で説明するコンポーネントは、ユーザーがページまたはコンポーネントに表示する内容を宣言的に制御する方法を提供します。

(サーバーアプリケーションで) ユーザーと要求を操作するに Blazor は、 `UserManager<T>` `IdentityUser` ユーザーの要求を列挙および変更するために使用できる (既定で使用する) を挿入することも必要になる場合があります。 最初に型を挿入し、それをプロパティに割り当てます。

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

次に、それを使用してユーザーの要求を処理します。 次のサンプルは、ユーザーにクレームを追加して永続化する方法を示しています。

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

ロールを使用する必要がある場合は、同じアプローチに従います。 `RoleManager<T>` `IdentityRole` ロール自体の一覧表示と管理には、(既定の型に使用) を挿入する必要がある場合があります。

**注:**BlazorWebassembly では、これらの操作を実行するためにサーバー api を提供する必要があります (またはを直接使用するので `UserManager<T>` はなく `RoleManager<T>` )。 BlazorWebassembly アプリケーションは、この目的のために公開されている API エンドポイントを安全に呼び出すことによって、信頼性情報や役割を管理します。

### <a name="migration-guide"></a>移行ガイド

ASP.NET Web フォームとユニバーサルプロバイダーから ASP.NET Core Id に移行するには、いくつかの手順を実行する必要があります。

1. ASP.NET Core Id データベーススキーマを転送先データベースに作成する
2. ユニバーサルプロバイダースキーマから ASP.NET Core Id スキーマにデータを移行する
3. からミドルウェアおよびサービスに構成を移行します。通常は、 `web.config``Startup.cs`
4. コントロールと条件を使用して個々のページを更新し、タグヘルパーと新しい id Api を使用します。

以下のセクションでは、これらの各手順について詳しく説明します。

### <a name="creating-the-aspnet-core-identity-schema"></a>ASP.NET Core Id スキーマの作成

ASP.NET Core Id に使用される必要なテーブル構造を作成するには、いくつかの方法があります。 最も簡単なのは、新しい ASP.NET Core Web アプリケーションを作成することです。 [Web アプリケーション] を選択し、個々のユーザーアカウントを使用するように認証を変更します。

![個々のユーザーアカウントを持つ新しいプロジェクト](./media/security/individual-user-accounts.png)

コマンドラインからを実行すると、同じことを行うことができ `dotnet new webapp -au Individual` ます。 アプリが作成されたら、それを実行し、サイトに登録します。 次のようなページをトリガーする必要があります。

![[移行の適用] ページ](./media/security/apply-migrations-page.png)

[移行の適用] ボタンをクリックすると、必要なデータベーステーブルが作成されます。 また、次のように、移行ファイルがプロジェクトに表示されます。

![移行ファイル](./media/security/migration-files.png)

次のコマンドラインツールを使用すると、web アプリケーションを実行しなくても、自分で移行を実行できます。

```powershell
dotnet ef database update
```

新しいスキーマを既存のデータベースに適用するスクリプトを実行する場合は、コマンドラインからこれらの移行をスクリプト化することができます。 次のコマンドを実行して、スクリプトを生成します。

```powershell
dotnet ef migrations script -o auth.sql
```

上記のコマンドを実行すると、出力ファイルに SQL スクリプトが生成され `auth.sql` 、任意のデータベースに対して実行できます。 コマンドの実行で問題が発生した場合は、 `dotnet ef` [EF Core ツールがシステムにインストールされ](/ef/core/miscellaneous/cli/dotnet)ていることを確認してください。

ソーステーブルに列が追加されている場合は、新しいスキーマでこれらの列の最適な場所を特定する必要があります。 一般に、テーブルで見つかった列は `aspnet_Membership` テーブルにマップする必要があり `AspNetUsers` ます。 の列 `aspnet_Roles` をにマップする必要があり `AspNetRoles` ます。 テーブルのその他の列 `aspnet_UsersInRoles` がテーブルに追加され `AspNetUserRoles` ます。

また、別のテーブルに列を追加することも検討してください。 そのため、今後の移行では、既定の id スキーマのカスタマイズを考慮する必要がありません。

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a>ユニバーサルプロバイダーから ASP.NET Core Id へのデータの移行

変換先テーブルスキーマを配置したら、次の手順では、ユーザーとロールのレコードを新しいスキーマに移行します。 スキーマの相違点 (どの列がどの新しい列にマップされているかなど) の完全な一覧については、 [こちら](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)を参照してください。

メンバーシップから新しい id テーブルにユーザーを移行するには、 [ドキュメントに記載](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)されている手順に従う必要があります。 次の手順とスクリプトを実行した後、ユーザーは次回ログインするときにパスワードを変更する必要があります。

ユーザーのパスワードを移行することはできますが、プロセスはさらに複雑になります。 移行プロセスの一環としてユーザーがパスワードを更新する必要があり、新しい一意のパスワードを使用するように勧めることは、アプリケーションの全体的なセキュリティを強化することです。

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a>web.config から Startup.cs へのセキュリティ設定の移行

前述のように、ASP.NET のメンバーシップとロールプロバイダーは、アプリケーションのファイルで構成され `web.config` ます。 ASP.NET Core アプリは IIS に関連付けられていないため、構成に別のシステムを使用するため、これらの設定は別の場所で構成する必要があります。 ほとんどの場合、ASP.NET Core Id はファイルで構成され `Startup.cs` ます。 (Id テーブルスキーマを生成するために) 前に作成した web プロジェクトを開き、そのファイルを確認し `Startup.cs` ます。

既定の ConfigureServices メソッドは、EF Core と Id のサポートを追加します。

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

`AddDefaultIdentity`拡張メソッドは、既定のとフレームワークの型を使用するように id を構成するために使用され `ApplicationDbContext` `IdentityUser` ます。 カスタムを使用している場合は `IdentityUser` 、ここでその型を指定してください。 これらの拡張メソッドがアプリケーションで動作していない場合は、適切な using ステートメントがあることと、必要な NuGet パッケージ参照があることを確認してください。 たとえば、プロジェクトにはいくつかのバージョンのおよびパッケージが参照されている必要があり `Microsoft.AspNetCore.Identity.EntityFrameworkCore` `Microsoft.AspNetCore.Identity.UI` ます。

また、 `Startup.cs` サイトに必要なミドルウェアが構成されていることがわかります。 具体的には、 `UseAuthentication` とは `UseAuthorization` 適切な場所に設定されている必要があります。

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
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

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

ASP.NET Identity は、からの場所への匿名またはロールベースのアクセスを構成しません `Startup.cs` 。 ASP.NET Core のフィルターには、場所固有の承認構成データを移行する必要があります。 このような更新が必要なフォルダーとページをメモしておきます。 これらの変更は、次のセクションで行います。

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a>ASP.NET Core Id の抽象化を使用するように個々のページを更新する

ASP.NET Web フォームアプリケーションで、 `web.config` 匿名ユーザーに特定のページまたはフォルダーへのアクセスを拒否する設定があった場合、その `[Authorize]` ようなページに属性を追加することによって、これらの変更を移行します。

```razor
@attribute [Authorize]
```

特定のロールに属しているユーザー以外のアクセスを拒否した場合は、ロールを指定する属性を追加して、この動作を移行することもできます。

```razor
@attribute [Authorize(Roles ="administrators")]
```

属性は、 `[Authorize]` `@page` ルーター経由で到達したコンポーネントに対してのみ機能し Blazor ます。 属性は子コンポーネントでは使用できませんが、代わりにを使用する必要があり `AuthorizeView` ます。

特定のユーザーにコードを表示するかどうかを判断するためのロジックがページマークアップ内にある場合は、これをコンポーネントで置き換えることができ `AuthorizeView` ます。 [Authorizeview コンポーネント](/aspnet/core/blazor/security#authorizeview-component)は、ユーザーが表示を許可されているかどうかに応じて、UI を選択的に表示します。 また、 `context` ユーザー情報へのアクセスに使用できる変数も公開されています。

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

`Task<AuthenticationState`属性を使用して構成されたからユーザーにアクセスすることで、手続き型ロジック内の認証状態にアクセスでき `[CascadingParameter]` ます。 この構成を使用すると、ユーザーにアクセスできるようになります。認証されているかどうか、および特定のロールに属しているかどうかを確認できます。 ポリシー procedurally を評価する必要がある場合は、のインスタンスを挿入 `IAuthorizationService` し、そのインスタンスでメソッドを呼び出すことができ `AuthorizeAsync` ます。 次のサンプルコードは、ユーザー情報を取得し、承認されたユーザーがポリシーによって制限されたタスクを実行することを許可する方法を示して `content-editor` います。

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

最初のは、 `AuthenticationState` このようなカスケード型のパラメーターにバインドする前に、カスケード値として設定する必要があります。 通常、これはコンポーネントを使用し `CascadingAuthenticationState` ます。 通常、この構成は次のように行われ `App.razor` ます。

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a>まとめ

Blazor では、ASP.NET Core Id である ASP.NET Core と同じセキュリティモデルを使用します。 カスタマイズが元のデータスキーマに適用されていないと仮定すると、ユニバーサルプロバイダーから ASP.NET Core Id への移行は比較的簡単です。 データが移行されたら、アプリでの認証と承認の使用に Blazor ついて詳しく説明されています。また、ほとんどのセキュリティ要件をプログラムによってサポートすることもできます。

## <a name="references"></a>References

- [ASP.NET Core での Id の概要](/aspnet/core/security/authentication/identity)
- [ASP.NET メンバーシップ認証から ASP.NET Core 2.0 Id に移行する](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [認証と Id を ASP.NET Core に移行する](/aspnet/core/migration/identity)
- [Blazor認証と承認の ASP.NET Core](/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
>[前へ](config.md)
>[次へ](migration.md)
