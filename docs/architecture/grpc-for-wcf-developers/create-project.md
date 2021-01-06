---
title: WCF 開発者向けの新しい ASP.NET Core gRPC プロジェクト-gRPC を作成する
description: Visual Studio またはコマンドラインを使用して gRPC プロジェクトを作成する方法について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: 960725a9507797f43b2c15283e384b0ad827c2b1
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938658"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>新しい ASP.NET Core gRPC プロジェクトを作成する

.NET SDK には、強力な CLI ツールであるが付属しています。このツールを使用すると、 `dotnet` コマンドラインからプロジェクトとソリューションを作成および管理できます。 SDK は Visual Studio と密接に統合されているので、使い慣れたグラフィカルユーザーインターフェイスを使用してすべてを利用できます。 この章では、新しい ASP.NET Core gRPC プロジェクトを作成する両方の方法について説明します。

## <a name="create-the-project-by-using-visual-studio"></a>Visual Studio を使用してプロジェクトを作成する

> [!IMPORTANT]
> ASP.NET Core 5.0 アプリを開発するには、 **ASP.NET と web 開発** ワークロードがインストールされた Visual Studio 2019 バージョン16.3 以降が必要です。

空の *ソリューション* テンプレートから、 **TraderSys** という名前の空のソリューションを作成します。 という名前のソリューションフォルダーを追加 `src` します。 次に、フォルダーを右クリックし、[   >  **新しいプロジェクト** の追加] を選択します。 [ `grpc` テンプレート検索] ボックスに「」と入力すると、という名前のプロジェクトテンプレートが表示され `gRPC Service` ます。

![[新しいプロジェクトの追加] ダイアログボックスのスクリーンショット](media/create-project/new-grpc-project.png)

[ **次** へ] を選択して、[ **新しいプロジェクトの構成** ] ダイアログボックスに進みます。 プロジェクトに名前 `TraderSys.Portfolios` を指定し `src` 、その **場所** にサブディレクトリを追加します。

![[新しいプロジェクトの構成] ダイアログボックスのスクリーンショット](media/create-project/configure-project.png)

[ **次** へ] を選択して、[ **新しい Grpc サービスの作成** ] ダイアログボックスに進みます。

![[新しい gRPC サービスの作成] ダイアログボックスのスクリーンショット](media/create-project/create-new-grpc-service-v2.png)

現時点では、サービス作成のオプションは限られています。 Docker は後で導入されるため、このオプションをオフのままにしておきます。 [作成] を選択 **する** だけです。 最初の ASP.NET Core 5.0 gRPC プロジェクトが生成され、ソリューションに追加されます。 の使用について知りたくない場合は、 `dotnet CLI` 「 [コード例のクリーンアップ](#clean-up-the-example-code) 」のセクションに進んでください。

## <a name="create-the-project-by-using-the-net-cli"></a>.NET CLI を使用してプロジェクトを作成する

ここでは、コマンドラインからのソリューションとプロジェクトの作成について説明します。

次のコマンドに示すように、ソリューションを作成します。 `-o`(または `--output` ) フラグは、現在のディレクトリに作成されている出力ディレクトリを指定します (まだ存在しない場合)。 ソリューションには、ディレクトリと同じ名前が付けられてい `TraderSys.sln` ます。 `-n`(または) フラグを使用して、別の名前を指定でき `--name` ます。

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 5.0 には、gRPC サービス用の CLI テンプレートが付属しています。 このテンプレートを使用して新しいプロジェクトを作成し、 `src` ASP.NET Core プロジェクトの従来のようにサブディレクトリに配置します。 フラグを使用して別の名前を指定しない限り、プロジェクトにはディレクトリ () の後に名前が付けられ `TraderSys.Portfolios.csproj` `-n` ます。

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

最後に、コマンドを使用して、ソリューションにプロジェクトを追加し `dotnet sln` ます。

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> 特定のディレクトリにはファイルが1つしか含まれていないため、 `.csproj` ディレクトリだけを指定して入力を保存できます。

このソリューションは、Visual Studio 2019、Visual Studio Code、または任意のエディターで開くことができるようになりました。

## <a name="clean-up-the-example-code"></a>コード例をクリーンアップする

これで、このブックで既に確認されている gRPC テンプレートを使用して、サンプルサービスを作成できました。 このコードは、株式取引のコンテキストでは役に立たないので、最初のプロジェクトのために編集します。

### <a name="rename-and-edit-the-proto-file"></a>プロトコルファイルの名前を変更して編集する

ファイルの名前 `Protos/greet.proto` をに変更し `Protos/portfolios.proto` 、エディターで開きます。 行の後のすべてを削除 `package` します。 次に、 `option csharp_namespace` 、、 `package` およびの `service` 名前を変更し、既定のサービスを削除し `SayHello` ます。 コードは次のようになります。

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> 既定では、このテンプレートでは名前空間の部分は追加されません `Protos` が、追加すると、gRPC によって生成されたクラスと独自のクラスをコード内で明確に区別しやすくなります。

`greet.proto`Visual Studio などの統合開発環境 (IDE) でファイルの名前を変更すると、このファイルへの参照がファイルで自動的に更新され `.csproj` ます。 ただし、Visual Studio Code などの他のエディターでは、この参照は自動的に更新されないため、プロジェクトファイルを手動で編集する必要があります。

GRPC ビルドターゲットには、どのファイルをコンパイルするかを `Protobuf` 指定できる item 要素 `.proto` と、どのような形式のコード生成が必要か (つまり、"サーバー" または "クライアント") があります。

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>クラスの名前を変更する `GreeterService`

`GreeterService`クラスはフォルダー内に `Services` あり、から継承され `Greeter.GreeterBase` ます。 名前をに変更 `PortfolioService` し、基本クラスをに変更し `Portfolios.PortfoliosBase` ます。 メソッドを削除 `override` します。

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

クラスのメソッドに、クラスへの参照がありました `GreeterService` `Configure` `Startup` 。 リファクタリングを使用してクラスの名前を変更した場合は、この参照が自動的に更新されている必要があります。 ただし、使用していない場合は、手動で編集する必要があります。

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

次のセクションでは、この新しいサービスに機能を追加します。

>[!div class="step-by-step"]
>[前へ](migrate-wcf-to-grpc.md)
>[次へ](migrate-request-reply.md)
