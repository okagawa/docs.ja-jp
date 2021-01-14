---
title: Linux コンテナーとして AKS/Kubernetes クラスターにデプロイされる ASP.NET Core アプリケーションをビルドする
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
ms.date: 01/06/2021
ms.openlocfilehash: 7a8f8272ab2faabd0398aeeb2039b6f034b4dedb
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970648"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Linux コンテナーとして AKS/Kubernetes オーケストレーターにデプロイされる ASP.NET Core アプリケーションをビルドする

Azure Kubernetes Services (AKS) は、Azure のマネージド Kubernetes オーケストレーション サービスであり、コンテナーのデプロイと管理を簡略化します。

AKS の主な機能は次のとおりです。

- Azure でホストされるコントロール プレーン
- 自動アップグレード
- 自己復旧
- ユーザーが構成可能なスケーリング
- 開発者とクラスター オペレーターの両方のよりシンプルなユーザー エクスペリエンス。

次の例では、Linux で実行され、Azure の AKS クラスターにデプロイされる、ASP.NET Core 5.0 アプリケーションの作成について確認しますが、開発は Visual Studio 2019 バージョン 16.8 を使用して行われています。

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a>Visual Studio 2019 を使用する ASP.NET Core プロジェクトの作成

ASP.NET Core は、GitHub で Microsoft および .NET コミュニティによって管理される汎用開発プラットフォームです。 これはクロスプラットフォームであり、Windows、macOS、Linux がサポートされ、デバイス、クラウド、および埋め込み/IoT シナリオで使用できます。

この例では、Visual Studio テンプレートに基づくいくつかのシンプルなプロジェクトを使用します。したがって、サンプルを作成するための多くの追加の知識は必要ありません。 ASP.NET Core 5.0 テクノロジを使用し、Razor Pages で Web アプリおよび REST API で小さなプロジェクトを実行するための要素をすべて含む、標準テンプレートを使ってプロジェクトを作成するだけで済みます。

![ASP.NET Core Web アプリケーションが選択されている、Visual Studio の新しいプロジェクトの追加ウィンドウ。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

**図 4-35**. Visual Studio 2019 での ASP.NET Core Web アプリケーションの作成。

Visual Studio でサンプル プロジェクトを作成するには、 **[ファイル]**  >  **[新規]**  >  **[プロジェクト]** の順に選択し、プロジェクトの種類として **[Web]** を選んでから **[ASP.NET Core Web アプリケーション]** テンプレートを選択します。 必要に応じて、テンプレートを検索することもできます。

その後、次の図に示すように、アプリケーションの名前と場所を入力します。

![プロジェクト名と場所を入力する。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

**図 4-36**. Visual Studio 2019 でプロジェクト名と場所を入力する。

ASP.NET Core 5.0 をフレームワークとして選択したことを確認します。 .NET 5.0 は最新リリースの Visual Studio 2019 に含まれており、Visual Studio のインストール時に自動的にインストールされ、構成されます。

![API オプションが選択された状態の、ASP.NET Core Web アプリケーションの種類を選択するための Visual Studio ダイアログ。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

**図 4-37**. ASP.NET Core 5.0 と Web API プロジェクトの種類の選択

現在、Docker のサポートが有効になっておらず、単にプロジェクトの作成後に実行できることが示されていることに注目してください。

以前のバージョンの .NET Core をお持ちの場合は、<https://dotnet.microsoft.com/download> から 3.1 のバージョンをダウンロードしてインストールすることができます。

いつでもプロジェクトを "Docker でコンテナー化" できることを示すには、ここで Docker サポートを追加します。 したがって、ソリューション エクスプローラーでプロジェクト ノードを右クリックし、コンテキスト メニューで **[追加]**  >  **[Docker サポート]** の順に選択します。

![既存のプロジェクトに Docker サポートを追加するためのコンテキスト メニュー オプション:(プロジェクトを) 右クリック > [追加] > [Docker サポート]。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

**図 4-38**. 既存のプロジェクトへの Docker サポートの追加

Docker サポートの追加を完了するために、Windows または Linux を選択できます。 この場合は、 **[Linux]** を選択します。

![Dockerfile のターゲット OS を選択するためのオプション ダイアログ。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

**図 4-39**. Linux コンテナーの選択。

これらのシンプルな手順では、Linux コンテナーで実行される ASP.NET Core 5.0 アプリケーションを作成します。

同様に、Web API エンドポイントを使用するために、非常にシンプルな **WebApp** プロジェクトを追加することもできます (図 4-40)。しかし、詳細についてはここでは説明しません。

その後、次の図 4-40 に示すように、**WebApi** プロジェクトのオーケストレーター サポートを追加します。

![WebApi プロジェクトへのオーケストレーター サポートの追加](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

**図 4-40**. *WebApi* プロジェクトへのオーケストレーター サポートの追加。

ローカル開発に適している、`Docker Compose` オプションを選ぶと、図 4-41 に示すように、Visual Studio によって、docker-compose ファイルを含む docker-compose プロジェクトが追加されます。

![ソリューションに追加された docker-compose](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

**図 4-41**. *WebApi* プロジェクトへのオーケストレーター サポートの追加。

追加される初期ファイルはこのようなものです。

`docker-compose.yml`

```yml
version: "3.4"

services:
  webapi:
    image: ${DOCKER_REGISTRY-}webapi
    build:
      context: .
      dockerfile: WebApi/Dockerfile

  webapp:
    image: ${DOCKER_REGISTRY-}webapp
    build:
      context: .
      dockerfile: WebApp/Dockerfile
```

`docker-compose.override.yml`

```yml
version: "3.4"

services:
  webapi:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
  webapp:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
```

Docker Compose でアプリを実行する場合は、`docker-compose.override.yml` に対して微調整をいくつか行うだけで済みます

```yml
services:
  webapi:
    #...
    ports:
      - "51080:80"
      - "51443:443"
    #...
  webapp:
    environment:
      #...
      - WebApiBaseAddress=http://webapi
    ports:
      - "50080:80"
      - "50443:443"
    #...
```

これで、**F5** キーを使い、または図 4-42 に示すように **[再生]** ボタンか、あるいは **Ctrl + F5** キーを使用して、docker-compose プロジェクトを選択し、アプリケーションを実行できます。

![Visual Studio での docker-compose プロジェクトの実行](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

**図 4-42**. *WebApi* プロジェクトへのオーケストレーター サポートの追加。

説明に従って docker-compose アプリケーションを実行すると、次のようになります。

1. docker-compose ファイルに従って、イメージがビルドされ、コンテナーが作成されます。
2. `docker-compose` プロジェクトの [プロパティ] ダイアログで構成されたアドレスで、ブラウザーが開きます。
3. (Visual Studio 2019 バージョン 16.4 以降で) **[コンテナー]** ウィンドウが開きます。
4. 次の図に示すように、ソリューション内のすべてのプロジェクトに対してデバッガーがサポートされます。

開かれたブラウザー:

![実行されている Web アプリを示すブラウザー ビュー](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

**図 4-43**. 複数のコンテナーで実行されるアプリケーションを示すブラウザー ウィンドウ。

[コンテナー] ウィンドウ:

![Visual Studio の [コンテナー] ウィンドウ](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

**図 4-44**. Visual Studio の [コンテナー] ウィンドウ

**[コンテナー]** ウィンドウを使用すれば、実行中のコンテナーの表示、使用可能なイメージの参照、環境変数、ログ、およびポート マッピングの表示、ファイルシステムの検査、デバッガーのアタッチを行ったり、コンテナー環境内でターミナル ウィンドウを開いたりすることができます。

おわかりのように、Visual Studio 2019 と Docker 間の統合は完全に開発者の生産性を重視して行われています。

もちろん、`docker images` コマンドを使用してイメージを一覧表示することもできます。 Visual Studio 2019 でのプロジェクトの自動デプロイによって作成された、タグが `dev` の `webapi` および `webapp` イメージが表示されるはずです。

```console
docker images
```

![docker images コマンドからのコンソール出力には、以下のものを含むリストが表示されます:リポジトリ、タグ、イメージ ID、作成 (日)、およびサイズ。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

**図 4-45**. Docker イメージのビュー

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a>Azure Container Registry (ACR) にソリューションを登録する

[Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) にイメージをアップロードできますが、Docker Hub またはその他のレジストリを使用して、イメージをそのレジストリから AKS クラスターにデプロイすることもできます。

### <a name="create-an-acr-instance"></a>ACR インスタンスを作成する

**az cli** から、次のコマンドを実行します。

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

> [!NOTE]
> コンテナー レジストリ名 (`exploredocker` など) は、Azure 内で一意にし、5 から 50 文字の英数字を含める必要があります。 詳細については、「[コンテナー レジストリの作成](/azure/container-registry/container-registry-get-started-azure-cli#create-a-container-registry)」を参照してください。

### <a name="create-the-image-in-release-mode"></a>リリース モードでイメージを作成する

ここでは、図 4-46 に示すように、 **[リリース]** に変更し、前と同じようにアプリケーションを実行して、**リリース** モード (運用環境の準備ができている) でイメージを作成します。

![リリース モードでビルドするための VS のツール バー オプション。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

**図 4-46**. リリース モードの選択

`docker images` コマンドを実行すると、作成された両方のイメージが表示されます。1 つは `debug` (**開発**) 用で、もう 1 つは `release` (**最新**) モード用です。

### <a name="create-a-new-tag-for-the-image"></a>イメージの新しいタグを作成する

各コンテナー イメージは、レジストリの名前 `loginServer` でタグ付けする必要があります。 このタグは、イメージ レジストリにコンテナー イメージをプッシュするときに、ルーティングするために使用されます。

Azure Container Registry から情報を取得し、Azure portal から `loginServer` という名前を表示できます

![右上に Azure Container Registry の名前が示されているブラウザー ビュー。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

**図 4-47**. レジストリの名前のビュー

または、次のコマンドを実行します。

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![上記のコマンドからのコンソール出力。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

**図 4-48**. **az cli** を使用してレジストリの名前を取得する

いずれの場合も、名前を取得します。 この例では、`exploredocker.azurecr.io` です。

これで、コマンドを使用し、最新のイメージ (リリース イメージ) を取得して、イメージにタグを付けることができます。

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

`docker tag` コマンドを実行した後、`docker images` コマンドを使ってイメージをリストすると、新しいタグが付いたイメージが表示されるはずです。

![docker images コマンドからのコンソール出力。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

**図 4-49**. タグが付けられたイメージのビュー

### <a name="push-the-image-into-the-azure-acr"></a>Azure ACR にイメージをプッシュする

Azure Container Registry にログインします

```console
az acr login --name exploredocker
```

次のコマンドを使用して、Azure ACR にイメージをプッシュします。

```console
docker push <login-server-name>/<image-name>:v1
```

このコマンドでのイメージのアップロードにはしばらく時間がかかりますが、プロセス時にフィードバックが提供されます。 次の図により、1 つのイメージからの出力が完了しており、もう 1 つは進行中であることがわかります。

![docker push コマンドからのコンソール出力。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

**図 4-50** push コマンドからのコンソール出力。

複数コンテナー アプリを AKS クラスターにデプロイするには、`docker-compose.yml` および `docker-compose.override.yml` ファイルから取得されたほとんどのプロパティを含む、マニフェスト `.yaml` ファイルがいくつか必要です。

#### `deploy-webapi.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapi
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapi
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapi
    spec:
      containers:
        - name: webapi
          image: exploredocker.azurecr.io/webapi:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
---
apiVersion: v1
kind: Service
metadata:
  name: webapi
  labels:
    app: weather-forecast
    service: webapi
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapi
```

#### `deploy-webapp.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapp
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapp
    spec:
      containers:
        - name: webapp
          image: exploredocker.azurecr.io/webapp:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
            - name: WebApiBaseAddress
              value: http://webapi
---
apiVersion: v1
kind: Service
metadata:
  name: webapp
  labels:
    app: weather-forecast
    service: webapp
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapp
```

> [!NOTE]
> 上記の `.yml` ファイルの場合、`ASPNETCORE_URLS` パラメーターが使用され、`HTTP` ポートのみが有効になり、サンプル アプリの証明書の欠落に関する問題を回避できます。

> [!TIP]
> このガイドの「[**Azure Kubernetes Service (AKS) へのデプロイ**](deploy-azure-kubernetes-service.md)」セクションで、このサンプル用の AKS クラスターを作成する方法を確認できます。

これで、**kubectl** を使用してデプロイする準備がほぼ整いましたが、最初にこのコマンドを使用して、AKS クラスターから資格情報を取得する必要があります。

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![上記のコマンドからのコンソール出力:C:\Users\Miguel.kube\config の現在のコンテキストとしてマージされた "explore-docker-aks"](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

**図 4-51** AKS から kubectl 環境への資格情報の取得。

また、このコマンドを使用して、AKS クラスターで ACR からイメージをプルできるようにする必要もあります。

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

上記のコマンドの実行には数分かかる場合があります。 その後、`kubectl apply` コマンドを使用してデプロイを起動してから、`kubectl get all` を使用してクラスター オブジェクトの一覧を取得します。

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![上記のコマンドからのコンソール出力: 適用されたデプロイ。 作成されたサービス。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

**図 4-52** Kubernetes へのデプロイ

ロード バランサーによって外部 IP が取得され、`kubectl get services` で確認されるまでしばらく待機する必要があります。その後、次の図に示すように、そのアドレスでアプリケーションを使用できるはずです。

![AKS にデプロイされたアプリケーションのブラウザー ビュー](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

**図 4-53** Kubernetes へのデプロイ

デプロイが完了したら、ssh トンネルを使用して、ローカル プロキシで [Kubernetes Web UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) にアクセスできます。

まず、次のコマンドを使用して ClusterRoleBinding を作成する必要があります。

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

その後、このコマンドを実行してプロキシを開始します。

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

ブラウザー ウィンドウが `http://127.0.0.1:8001` で開き、このようなビューが表示されるはずです。

![デプロイ、ポッド、レプリカ セット、サービスを示す、Kubernetes ダッシュボードのブラウザー ビュー。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

**図 4-54** Kubernetes クラスターの情報を表示する

これで、Linux コンテナーで実行される ASP.NET Core アプリケーションが作成され、Azure 上の AKS クラスターにデプロイされました。

> [!NOTE]
> Kubernetes を使用するデプロイの詳細については、<https://kubernetes.io/docs/reference/kubectl/cheatsheet/> を参照してください

> [!div class="step-by-step"]
> [前へ](set-up-windows-containers-with-powershell.md)
> [次へ](../docker-devops-workflow/index.md)
