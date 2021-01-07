---
title: WCF 開発者向け Docker-gRPC
description: ASP.NET Core gRPC アプリケーション用の Docker イメージの作成
ms.date: 01/06/2021
ms.openlocfilehash: f59518a28b0a1dee75c792ba03bd4af826638502
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970090"
---
# <a name="create-docker-images"></a>Docker イメージを作成する

このセクションでは、ASP.NET Core gRPC アプリケーション用の Docker イメージを作成する方法について説明します。 Docker、Kubernetes、またはその他のコンテナー環境で実行できます。 ASP.NET Core MVC web アプリおよび gRPC サービスと共に使用されるサンプルアプリケーションは、GitHub の [dotnet/grpc-wcf 開発者](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) リポジトリで入手できます。

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>ASP.NET Core アプリケーション用の Microsoft 基本イメージ

Microsoft では、.NET アプリケーションをビルドして実行するためのさまざまな基本イメージを提供しています。 ASP.NET Core 5.0 イメージを作成するには、次の2つの基本イメージを使用します。

- アプリケーションをビルドして発行するための SDK イメージ。
- 配置のランタイムイメージ。

| Image | 説明 |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/sdk](https://hub.docker.com/_/microsoft-dotnet-sdk/) | を使用してアプリケーションをビルド `docker build` します。 運用環境では使用されません。 |
| [mcr.microsoft.com/dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) | ランタイムと ASP.NET Core の依存関係を含みます。 運用環境向け。 |

各イメージには、タグによって識別される、異なる Linux ディストリビューションに基づく4つのバリエーションがあります。

| イメージタグ | Linux | Notes |
| --------- | ----- | ----- |
| 5.0-buster-スリム、5.0 | Debian 10 | OS バリアントが指定されていない場合の既定のイメージ。 |
| 5.0-アルペン | Alpine 3.12 | Alpine base イメージは Debian または Ubuntu よりもはるかに小さいものです。 |
| 5.0-焦点| Ubuntu 20.04 | |

Alpine base イメージは約 100 MB であり、Debian および Ubuntu イメージでは 200 MB と比較しています。 一部のソフトウェアパッケージまたはライブラリは、アルペンのパッケージ管理では利用できない場合があります。 使用するイメージがわからない場合は、既定の Debian を選択することをお勧めします。

> [!IMPORTANT]
> ビルドとランタイムに同じ形式の Linux を使用していることを確認します。 1つのバリアントでビルドおよび発行されたアプリケーションが、別のバリアントで動作しない可能性があります。

## <a name="create-a-docker-image"></a>Docker イメージを作成します。

Docker イメージは、 *Dockerfile* によって定義されます。 この *Dockerfile* は、アプリケーションを構築するために必要なすべてのコマンドを含むテキストファイルで、アプリケーションをビルドまたは実行するために必要なすべての依存関係をインストールします。 次の例は、ASP.NET Core 5.0 アプリケーションの最も単純な Dockerfile を示しています。

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build

WORKDIR /src

COPY ./StockKube.sln .
COPY ./src/StockData/StockData.csproj ./src/StockData/
COPY ./src/StockWeb/StockWeb.csproj ./src/StockWeb/

RUN dotnet restore

COPY . .

RUN dotnet publish --no-restore -c Release -o /published src/StockData/StockData.csproj

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=build /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

Dockerfile には、2つの部分があります。1つ目は基本イメージを使用してアプリケーションをビルドし、発行します。 `sdk` 2 つ目はベースからランタイムイメージを作成します。 `aspnet` これは、 `sdk` イメージは約 900 mb で、ランタイムイメージでは約 200 mb であり、ほとんどの内容は実行時には不要であるためです。

### <a name="the-build-steps"></a>ビルドステップ

| 手順 | 説明 |
| ---- | ----------- |
| `FROM ...` | 基本イメージを宣言し、エイリアスを割り当て `builder` ます。 |
| `WORKDIR /src` | ディレクトリを作成 `/src` し、現在の作業ディレクトリとして設定します。 |
| `COPY . .` | ホスト上の現在のディレクトリの下にあるものをすべて、イメージの現在のディレクトリにコピーします。 |
| `RUN dotnet restore` | 外部パッケージを復元します (ASP.NET Core 3.0 framework は SDK と共にプレインストールされています)。 |
| `RUN dotnet publish ...` | リリースビルドをビルドして発行します。 フラグは必須ではないことに注意 `--runtime` してください。 |

### <a name="the-runtime-image-steps"></a>ランタイムイメージの手順

| 手順 | 説明 |
| ---- | ----------- |
| `FROM ...` | 新しい基本イメージを宣言します。 |
| `WORKDIR /app` | ディレクトリを作成 `/app` し、現在の作業ディレクトリとして設定します。 |
| `COPY --from=builder ...` | 最初の行のエイリアスを使用して、発行されたアプリケーションを前のイメージからコピーし `builder` `FROM` ます。 |
| `ENTRYPOINT [ ... ]` | コンテナーの起動時に実行するコマンドを設定します。 `dotnet`ランタイムイメージ内のコマンドは、DLL ファイルのみを実行できます。 |

### <a name="https-in-docker"></a>Docker での HTTPS

Docker 用の Microsoft 基本イメージは `ASPNETCORE_URLS` 、環境変数をに設定し `http://+:80` ます。これは、Kestrel が HTTPS を使用せずにそのポートで実行されることを意味します。 ( [自己ホスト型 gRPC アプリケーション](self-hosted.md)で説明されているように) カスタム証明書で HTTPS を使用している場合は、この構成をオーバーライドする必要があります。 Dockerfile のランタイムイメージ作成部分で環境変数を設定します。

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:5.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Dockerignore ファイル

ソース管理から特定のファイルやディレクトリを除外するファイルと同じように、ファイルを使用して、 `.gitignore` `.dockerignore` ビルド中にファイルとディレクトリをイメージにコピーしないようにすることができます。 このファイルを使用すると、時間を節約できるだけでなく、 `obj` PC からのディレクトリがイメージにコピーされることによって発生するエラーを回避することもできます。 少なくとも、ファイルにとのエントリを追加する必要があり `bin` `obj` `.dockerignore` ます。

```console
bin/
obj/
```

## <a name="build-the-image"></a>イメージをビルドする

`StockKube.sln`2 つの異なるアプリケーションとが含まれているソリューションでは `StockData` `StockWeb` 、1つの dockerfile をベースディレクトリに配置するのが最も簡単です。 この場合、イメージをビルドするには、ファイルが `docker build` 置かれているディレクトリから次のコマンドを使用し `.sln` ます。

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

紛らわしい名前付き `--tag` フラグ (に短縮できます) は、 `-t` 指定されている場合は、イメージの完全な名前 (実際のタグを含む) を指定します。 `.`末尾のは、ビルドを実行するコンテキストを指定します。 Dockerfile 内のコマンドの現在の作業ディレクトリです `COPY` 。

1つのソリューション内に複数のアプリケーションがある場合は、各アプリケーションの Dockerfile を、ファイルの横にある独自のフォルダーに保持でき `.csproj` ます。 引き続き、 `docker build` ベースディレクトリからコマンドを実行して、ソリューションとすべてのプロジェクトがイメージにコピーされるようにする必要があります。 `--file`(または) フラグを使用して、現在のディレクトリの下に Dockerfile を指定でき `-f` ます。

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>コンピューターのコンテナーでイメージを実行する

ローカルの Docker インスタンスでイメージを実行するには、コマンドを使用し `docker run` ます。

```console
docker run -ti -p 5000:80 stockdata:1.0.0
```

フラグは、 `-ti` 現在のターミナルをコンテナーのターミナルに接続し、対話モードで実行します。 は、 `-p 5000:80` コンテナーのポート80を localhost ネットワークインターフェイスのポート5000に発行 (リンク) します。

## <a name="push-the-image-to-a-registry"></a>イメージをレジストリにプッシュする

イメージが動作することを確認したら、それを Docker レジストリにプッシュして、他のシステムで使用できるようにします。 内部ネットワークでは、Docker レジストリをプロビジョニングする必要があります。 このアクティビティは、 [docker の独自の `registry` イメージ](https://docs.docker.com/registry/deploying/) を実行するのと同じように簡単に行うことができます (Docker レジストリは docker コンテナーで実行されます) が、さまざまな包括的なソリューションを利用できます。 外部共有とクラウド使用については、 [Azure Container Registry](/azure/container-registry/) や [Docker Hub](https://docs.docker.com/docker-hub/repos/)などのさまざまな管理対象レジストリを利用できます。

Docker Hub にプッシュするには、イメージ名の前にユーザー名または組織名を付けます。

```console
docker tag stockdata:1.0.0 <myorg>/stockdata:1.0.0
docker push <myorg>/stockdata:1.0.0
```

プライベートレジストリにプッシュするには、イメージ名の前にレジストリのホスト名と組織名を付けます。

```console
docker tag stockdata <internal-registry:5000>/<myorg>/stockdata:1.0.0
docker push <internal-registry:5000>/<myorg>/stockdata:1.0.0
```

イメージがレジストリに格納された後、個々の Docker ホスト、または Kubernetes のようなコンテナーオーケストレーションエンジンにイメージを展開できます。

>[!div class="step-by-step"]
>[前へ](self-hosted.md)
>[次へ](kubernetes.md)
