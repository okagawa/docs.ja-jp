---
title: Docker アプリの内部ループ開発ワークフロー
description: Docker アプリケーションの "内部ループ" 開発ワークフローについて説明します。
ms.date: 01/06/2021
ms.openlocfilehash: 78c593890d56a6888d4c4ea6752497918222ebee
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970586"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker アプリの内部ループ開発ワークフロー

DevOps サイクル全体にまたがる外部ループ ワークフローをトリガーする前に、各内部ループが各開発者のコンピューターで開始され、アプリ自体をコード化し、希望する言語またはプラットフォームを使用し、ローカルでテストされます (図 4-21)。 ただし、すべての場合において、選択する言語、フレームワーク、プラットフォームに関係なく、共通する重要な点が 1 つあります。 この特定のワークフローでは、Docker コンテナーを開発し、テストしますが、常に他の環境ではなくローカルで行います。

![内部ループ開発環境の概念を示す図。](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

**図 4-21** 内部ループの開発コンテキスト

Docker イメージのコンテナーまたはインスタンスには、以下のコンポーネントが含まれます。

- 選択したオペレーティング システム (Linux ディストリビューションや Windows など)

- 開発者が追加したファイル (アプリのバイナリなど)

- 構成 (環境の設定や依存関係など)

- Docker でどのプロセスを実行するかに関する指示

Docker をプロセスとして活用する内部ループ開発ワークフローを設定できます (詳細は次のセクションにあります)。 環境設定の初回手順は含まれていません。それは一度だけ実行すれば良いからです。

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Visual Studio Code と Docker CLI を使用し、Docker コンテナー内で 1 つのアプリをビルドする

アプリは自分のサービスと追加のライブラリ (依存関係) から構成されます。

図 4-22 では、Docker アプリをビルドするときに通常行う基本手順と各手順の詳細を確認できます。

![コンテナー化されたアプリを作成するために必要な 7 つの手順を示す図。](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

**図 4-22** Docker CLI を利用し、Docker でコンテナー化されたアプリケーションのワークフローの概要

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>手順 1: Visual Studio Code でコーディングを開始し、初回アプリ/サービス ベースラインを作成する

アプリケーションの開発方法は、Docker を使用しない場合と同じです。 違いは、開発中、ローカル環境 (Linux VM や Windows など) に配置されている Docker コンテナー内で実行されているアプリケーションやサービスを展開し、テストするということです。

**ローカル環境を設定する**

Mac または Windows 向けの最新版 Docker Desktop を使用すると、Docker アプリケーションをもっと簡単に開発できます。設定も簡単です。

> [!TIP]
> Docker Desktop for Windows の設定方法については、<https://docs.docker.com/docker-for-windows/> にお進みください。
>
> Docker Desktop for Mac の設定方法については、<https://docs.docker.com/docker-for-mac/> にお進みください。

また、Docker CLI の使用時、実際にアプリケーションを開発できるよう、コード エディターが必要です。

Microsoft からは Visual Studio Code が提供されます。これは Windows、Linux、macOS でサポートされている軽量のコード エディターであり、IntelliSense、[さまざまな言語のサポート](https://code.visualstudio.com/docs/languages/overview) (JavaScript、.NET、Go、Java、Ruby、Python、ほとんどの新しい言語)、[デバッグ](https://code.visualstudio.com/Docs/editor/debugging)、[Git との統合](https://code.visualstudio.com/Docs/editor/versioncontrol)、[拡張機能サポート](https://code.visualstudio.com/docs/extensions/overview)を提供します。 このエディターは、macOS および Linux の開発者に最適です。 Windows では、Visual Studio を使用することもできます。

> [!TIP]
> Windows、Linux、または macOS 用の Visual Studio Code をインストールする手順については、「<https://code.visualstudio.com/docs/setup/setup-overview/>」を参照してください。
>
> Docker for Mac の設定方法については、<https://docs.docker.com/docker-for-mac/> にお進みください。

Docker CLI を使用して、あらゆるコード エディターでコードを記述できますが、Docker 拡張機能と共に Visual Studio Code を使用すると、ワークスペースで `Dockerfile` ファイルや `docker-compose.yml` ファイルを簡単に作成できます。 Visual Studio Code IDE からタスクやスクリプトを実行し、下部の Docker CLI を使用して Docker コマンドを実行することもできます。

VS Code 用 Docker 拡張機能からは次の機能が提供されます。

- `Dockerfile` および `docker-compose.yml` ファイルの自動生成

- `docker-compose.yml` および `Dockerfile` ファイルの構文強調表示とツールチップ

- `Dockerfile` および `docker-compose.yml` ファイルの IntelliSense (入力候補)

- `Dockerfile` ファイルの Lint 処理 (エラーと警告)

- 最も一般的な Docker コマンドのコマンド パレット (F1) 統合

- イメージとコンテナーを管理するためのエクスプローラー統合

- DockerHub と Azure Container Registry から Azure App Service へのイメージのデプロイ

Docker 拡張機能をインストールするには、Ctrl + Shift + P キーを押しながら、「`ext install`」と入力し、Install Extension コマンドを実行して Marketplace 拡張機能一覧を表示します。 次に、図 4-23 のように、「**docker**」と入力して結果にフィルターを適用し、Docker Support 拡張機能を選択します。

![VS Code 用 Docker 拡張機能の表示。](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**図 4-23**.  Visual Studio Code で Docker 拡張機能をインストールする

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-nodejs-and-ruby"></a>手順 2: 既存のイメージ (プレーンな OS か、.NET、Node.js、Ruby などの開発環境) に関連する DockerFile を作成する

ビルドするカスタム イメージごとと、展開するコンテナーごとに `DockerFile` が必要になります。 アプリが 1 つのカスタム サービスで構成される場合、`DockerFile` が 1 つ必要になります。 ただし、(マイクロサービス アーキテクチャの場合のように) アプリが複数のサービスで構成される場合、サービスごとに `Dockerfile` が 1 つ必要になります。

`DockerFile` は通常、アプリまたはサービスのルート フォルダーに配置され、そのアプリまたはサービスを設定し、実行する方法を Docker に認識させるための必須のコマンドが含まれています。 `DockerFile` を作成し、コード (node.js や .NET など) とともにプロジェクトに追加できます。この環境が初めての場合、次のヒントをご覧ください。

> [!TIP]
> Docker コンテナーに関連する `Dockerfile` および `docker-compose.yml` ファイルを使用するとき、Docker 拡張機能を利用してガイドを表示することができます。 最終的には、このツールなしでこの種類のファイルを記述することになるでしょうが、Docker 拡張機能の使用は学習曲線を加速するので、開始点として推奨されます。

図 4-24 で、VS Code 用の Docker 拡張機能を使用して Docker ファイルをプロジェクトに追加する手順を確認できます。

1. コマンド パレットを開き、「**docker**」と入力してから、"**Add Docker Files to Workspace**" を選択します。
2. アプリケーション プラットフォーム (ASP.NET Core) の選択
3. オペレーティング システム (Linux) の選択
4. オプションの Docker Compose ファイルを含める
5. 公開するポート (80、443) を入力
6. プロジェクトを選択する

![Docker 拡張機能を使用して Docker ファイルを追加する手順](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**図 4-24** **Add Docker files to Workspace** コマンドで追加された Docker ファイル

DockerFile を追加するとき、(`FROM mcr.microsoft.com/dotnet/aspnet` を使用するなどして) 使用する基本の Docker イメージを指定します。 通常、[Docker Hub レジストリ](https://hub.docker.com/)にある公式リポジトリから得られる基本イメージ ([.NET 用のイメージ](https://hub.docker.com/_/microsoft-dotnet/)や [Node.js 用のイメージ](https://hub.docker.com/_/node/)など) を基礎にしてカスタム イメージをビルドします。

> [!TIP]
> アプリケーション内のすべてのプロジェクトに対してこの手順を繰り返す必要があります。 ただし、拡張機能によって、2 回目以降は生成された docker-compose ファイルを上書きするように求められます。 それを上書きしないように応答する必要があります。そうすると拡張機能によって個別の docker-compose ファイルが作成され、docker-compose を実行する前に手動でマージできます。

**_既存の公式 Docker イメージを使用する_**

バージョン番号を持つ言語スタックの公式イメージ リポジトリを使うと、同じ言語機能が (開発、テスト、運用環境など) すべてのコンピューターで使用できるようになります。

次は .NET コンテナー向けサンプル DockerFile です。

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

この場合、イメージは、`FROM mcr.microsoft.com/dotnet/aspnet:5.0` の行から、公式の ASP.NET Core Docker イメージ (Linux および Windows 用マルチアーキテクチャ) のバージョン 5.0 に基づいています (このトピックの詳細については、[ASP.NET Core Docker イメージ](https://hub.docker.com/_/microsoft-dotnet-aspnet/)に関するページと [.NET Docker イメージ](https://hub.docker.com/_/microsoft-dotnet/)に関するページを参照してください)。

DockerFile では、実行時に使用する TCP ポートをリッスンするように Docker に指示することもできます (ポート 80 や 443 など)。

使用している言語とフレームワークによっては、Dockerfile に別の構成設定を指定できます。 たとえば、`["dotnet", "WebMvcApplication.dll"]` を含む `ENTRYPOINT` 行では、.NET アプリケーションを実行するように Docker に指示します。 SDK と .NET CLI (`dotnet CLI`) を使用して .NET アプリケーションをビルドし、実行する場合、この設定は異なるものになります。 ここで重要なことは、ENTRYPOINT 行とその他の設定はアプリケーションに選択した言語とプラットフォームに依存するということです。

> [!TIP]
> .NET アプリケーション向け Docker イメージのビルド方法については、<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images> にお進みください。
>
> 独自のイメージをビルドする方法については、<https://docs.docker.com/engine/tutorials/dockerimages/> にお進みください。

**マルチアーキテクチャ イメージ リポジトリを使用する**

リポジトリの単一のイメージ名には、Linux イメージや Windows イメージなどのプラットフォーム バリアントを含めることができます。 この機能では、Microsoft (基本イメージの作成者) などのベンダーが、複数のプラットフォーム (つまり、Linux および Windows) に対応できるリポジトリを 1 つ作成できます。 たとえば、Docker Hub レジストリにある [dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) リポジトリでは、同じイメージ名を使用して Linux および Windows Nano Server をサポートしています。

Windows ホストから [dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) イメージをプルした場合、Windows バリアントがプルされ、同じイメージ名が Linux ホストからプルされた場合、Linux バリアントがプルされます。

**_基本イメージを一から作成する_**

Docker の[この記事](https://docs.docker.com/engine/userguide/eng-image/baseimages/)で説明されているように、独自の Docker 基本イメージを一から作成できます。 Docker を初めて使用するユーザーにはおそらく推奨されませんが、独自の基本イメージを設定するならそれは可能です。

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>手順 3: カスタム Docker イメージを作成し、それにサービスを埋め込む

アプリを構成するカスタム サービスごとに、関連イメージを作成する必要があります。 アプリが 1 つのサービスまたは Web アプリで構成されている場合、イメージは 1 つのみ必要です。

> [!NOTE]
> "外部ループ DevOps ワークフロー" を考慮すると、イメージがソース コードからそのグローバル環境で作成されるよう、ソース コードを Git リポジトリにプッシュするたびに (継続的インテグレーション)、自動化されたビルド プロセスによってイメージが作成されます。
>
> ただし、その外部ループ ルートへの移行を検討する前に、Docker アプリケーションが実際に適切に動作していることを確保して、ソース管理システム (Git など) に、適切に機能しない可能性のあるコードがプッシュされないようにする必要があります。
>
> そのため、各開発者はまず、内部ループ プロセス全体を行ってローカル テストし、それから、完全な機能または変更をソース コントロール システムにプッシュするまで開発を続けます。

ローカル環境で DockerFile を使用してイメージを作成するには、図 4-25 に示すように、docker build コマンドを使用します。あらかじめイメージにタグが付けられていて、簡単なコマンドでアプリケーション内のすべてのサービスのイメージをビルドできます。

![docker-compose build コマンドのコンソール出力を示すスクリーンショット。](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**図 4-25** docker build の実行

任意で、プロジェクト フォルダーから `docker build` を直接実行する代わりに、`dotnet publish` 実行コマンドを使用し、それから `docker build` を実行することで、まず、必要な .NET ライブラリで展開可能なフォルダーを生成できます。

この例では、`webapi:latest` という名前で Docker イメージが作成されます (`:latest` は特定のバージョンのようなタグです)。 いくつかのコンテナーで作成した Docker アプリケーション用に作成する必要のあるカスタム イメージごとにこの手順を行うことができます。 一方で、次のセクションでは、`docker-compose` を使用してこれをもっと簡単に行う方法を説明します。

図 4-26 に示すように、`docker images` コマンドを使用して、ローカル リポジトリ (開発コンピューター) の既存のイメージを検索できます。

![コマンド docker イメージからのコンソール出力。既存のイメージを確認できます。](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**図 4-26** docker images を使用した既存のイメージの表示

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>手順 4: 複数のサービスで Docker アプリケーションを構築するときに docker-compose.yml でサービスを定義する

`docker-compose.yml` ファイルを利用すると、次のセクションで説明するように、展開コマンドで構成済みアプリケーションとして展開する一連の関連サービスを定義できます。

メインまたはルート ソリューション フォルダーでそのファイルを作成します。この `docker-compose.yml` ファイルで確認できるものと同様のコンテンツが含まれているはずです。

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

この特定のケースでは、このファイルにより、Web API サービス (カスタム サービス)、Web アプリケーション、Redis サービス (人気のキャッシュ サービス) という 3 つのサービスが定義されます。 各サービスはコンテナーとして配置されます。そのため、それぞれに具体的な Docker イメージを使用する必要があります。 この特定のアプリケーションの場合、次のとおりです。

- Web API サービスは、`src/WebApi/Dockerfile` ディレクトリの DockerFile から構築されます。

- ホスト ポート 51080 は、`webapi` コンテナーの公開されているポート 80 に転送されます。

- Web API サービスは Redis サービスに依存しています。

- Web アプリケーションから内部アドレス `http://webapi` を使用して Web API サービスにアクセスします。

- Redis サービスによって、Docker Hub レジストリからプルされた[最新のパブリック redis イメージ](https://hub.docker.com/_/redis/)が使用されます。 [Redis](https://redis.io/) はサーバー側アプリケーション用として人気があるキャッシュ システムです。

### <a name="step-5-build-and-run-your-docker-app"></a>手順 5: Docker アプリをビルドし、実行する

アプリにコンテナーが 1 つしかない場合、必要な作業は Docker ホスト (VM または物理サーバー) にそれを展開して実行することだけになります。 ただし、アプリが複数のサービスで構成されている場合、_それを作成する_ 必要もあります。 別のオプションを見てみましょう。

**_オプション A:1 つのコンテナーまたはサービスを実行する_**

次に示すように docker run コマンドを使用し、Docker イメージを実行できます。

```console
docker run -t -d -p 50080:80 webapp:latest
```

この特定の配置の場合、ホストのポート 50080 に送信された要求を内部ポート 80 にリダイレクトします。

**_オプション B:複数コンテナー アプリケーションを作成し、実行する_**

ほとんどの企業のシナリオでは、Docker アプリケーションは複数のサービスから構成されます。 それらのケースでは、`docker-compose up` コマンド (図 4-27) を実行でき、先ほど作成した docker-compose.yml ファイルが使用されます。 このコマンドを実行すると、すべてのカスタム イメージがビルドされ、作成されたアプリケーションがそのすべての関連コンテナーと共に配置されます。

![docker-compose up コマンドからのコンソール出力。](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**図 4-27** "docker-compose up" コマンドの実行結果

VM を表現する図 4-28 で示すように、`docker-compose up` の実行後、Docker ホストにアプリケーションとその関連コンテナーを展開します。

![マルチコンテナー アプリケーションを実行する VM](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**図 4-28** Docker コンテナーが展開された VM

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>手順 6: Docker アプリケーションをローカル テストする (ローカル、CD VM で)

この手順は、アプリで何が実行されているかによって異なります。

1 つのコンテナーまたはサービスとして展開される単純な .NET Web API "Hello World" の場合、DockerFile に指定されている TCP ポートを指定し、サービスにアクセスするだけです。

Docker ホストでブラウザーを開き、そのサイトに移動します。図 4-29 に示すように、アプリ/サービスが実行中であることを確認できるはずです。

![ブラウザーに表示される localhost/API/values からの応答](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**図 4-29** ブラウザーを使用して Docker アプリケーションをローカルでテストする

ポート 50080 を使用していますが、内部ではポート 80 にリダイレクトされていることにご注意ください。これは、前に説明したように、`docker compose` でこのように配置されたためです。

このテストは、図 4-30 に示すように、ターミナルから CURL を使用してブラウザーを使って行うことができます。

![http://localhost:51080/WeatherForecast から取得された CURL の結果](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**図 4-30** CURL を使用した Docker アプリケーションのローカル テスト

**Docker で実行されているコンテナーをデバッグする**

Visual Studio Code では、Node.js かその他のプラットフォーム (.NET コンテナーなど) を使用している場合、Docker をデバッグできます。

次のセクションで説明するように、Windows または Mac 向けの Visual Studio の使用時、Docker で .NET または .NET Framework コンテナーをデバッグすることもできます。

> [!TIP]
> Node.js Docker コンテナーのデバッグの詳細については、<https://blog.docker.com/2016/07/live-debugging-docker/> と <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more> を参照してください。

> [!div class="step-by-step"]
> [前へ](docker-apps-development-environment.md)
> [次へ](visual-studio-tools-for-docker.md)
