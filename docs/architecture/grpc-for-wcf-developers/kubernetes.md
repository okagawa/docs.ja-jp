---
title: WCF 開発者向け Kubernetes-gRPC
description: Kubernetes クラスターで ASP.NET Core gRPC サービスを実行しています。
ms.date: 12/15/2020
ms.openlocfilehash: 0b457d6fa982b5f5b983194d4aedbff0eb782f36
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938061"
---
# <a name="kubernetes"></a>Kubernetes

Docker ホストでコンテナーを手動で実行することもできますが、信頼性の高い運用システムの場合は、コンテナーオーケストレーションエンジンを使用して、クラスター内の複数のサーバーで実行されている複数のインスタンスを管理することをお勧めします。 さまざまなコンテナーオーケストレーションエンジンが用意されています。これには、Kubernetes、Docker の群れ、Apache のシステムなどがあります。 しかし、これらのエンジンでは、Kubernetes ははるかに広く使用されているので、この章で重点的に説明します。

Kubernetes には、次の機能が含まれています。

- **スケジュール設定** では、クラスター内の複数のノードでコンテナーを実行し、使用可能なリソースのバランスの取れた使用状況を確保し、障害が発生した場合はコンテナーを実行したままにして、新しいバージョンのイメージまたは新しい構成へのローリング更新を処理します。
- **正常性チェック** は、コンテナーを監視してサービスを継続的に確認します。
- **DNS & サービス検出** は、クラスター内のサービス間のルーティングを処理します。
- 受信は、選択したサービスを外部 **に公開し**、一般にこれらのサービスのインスタンス間で負荷分散を行います。
- **リソース管理** は、ストレージなどの外部リソースをコンテナーにアタッチします。

この章では、ASP.NET Core gRPC サービスと、サービスを使用する web サイトを Kubernetes クラスターにデプロイする方法について詳しく説明します。 使用されるサンプルアプリケーションは、GitHub の [dotnet/grpc-wcf 開発者](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) リポジトリで入手できます。

## <a name="kubernetes-terminology"></a>Kubernetes の用語

Kubernetes は *desired state configuration* を使用します。この API は *ポッド*、*デプロイ*、*サービス* などのオブジェクトを表すために使用され、*コントロールプレーン* は *クラスター* 内のすべての *ノード* で目的の状態を実装します。 Kubernetes クラスターには、 *KUBERNETES API* を実行する *マスター* ノードがあります。このノードは、プログラムによって、またはコマンドラインツールを使用して通信できます `kubectl` 。 `kubectl` では、コマンドライン引数を使用してオブジェクトを作成および管理できますが、Kubernetes オブジェクトの宣言データを含む YAML ファイルで最適に動作します。

### <a name="kubernetes-yaml-files"></a>Kubernetes YAML ファイル

すべての Kubernetes YAML ファイルには、少なくとも3つの最上位レベルのプロパティがあります。

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

プロパティは、 `apiVersion` ファイルの対象となるバージョン (および API) を指定するために使用されます。 プロパティは、 `kind` YAML が表すオブジェクトの種類を指定します。 プロパティには `metadata` 、、、などのオブジェクトプロパティが含まれてい `name` `namespace` `labels` ます。

ほとんどの Kubernetes YAML ファイルには、 `spec` オブジェクトの作成に必要なリソースと構成を説明するセクションもあります。

### <a name="pods"></a>ポッド

ポッドは、Kubernetes での実行の基本単位です。 複数のコンテナーを実行できますが、1つのコンテナーを実行するためにも使用されます。 ポッドには、コンテナーに必要なすべてのストレージリソースと、ネットワークの IP アドレスも含まれています。

### <a name="services"></a>サービス

サービスは、ポッド (またはポッドのセット) を記述し、クラスター内でそれらにアクセスする手段を提供するメタオブジェクトです。たとえば、クラスター DNS サービスを使用して、サービス名をポッド IP アドレスのセットにマップすることができます。

### <a name="deployments"></a>デプロイメント

展開は、ポッドに *必要な状態* オブジェクトです。 ポッドを手動で作成した場合は、終了時に再起動されません。 デプロイは、現在の時点で実行する必要があるポッド、およびそれらのポッドのレプリカの数をクラスターに伝えるために使用されます。

### <a name="other-objects"></a>その他のオブジェクト

ポッド、サービス、および展開は、最も基本的なオブジェクトの種類のうちの3つにすぎません。 Kubernetes クラスターによって管理されるオブジェクトの種類は他にも多数あります。 詳細については、 [Kubernetes の概念](https://kubernetes.io/docs/concepts/) に関するドキュメントを参照してください。

### <a name="namespaces"></a>名前空間

Kubernetes クラスターは、数百または数千のノードに拡張し、同様の数のサービスを実行するように設計されています。 オブジェクト名が競合しないようにするために、名前空間を使用して、大きなアプリケーションの一部としてオブジェクトをグループ化します。 Kubernetes の独自のサービスは名前空間で実行さ `default` れます。 既定のオブジェクトまたはクラスター内の他のテナントとの潜在的な競合を避けるために、すべてのユーザーオブジェクトを独自の名前空間に作成する必要があります。

## <a name="get-started-with-kubernetes"></a>Kubernetes の概要

Windows 用の Docker Desktop または Mac 用 Docker デスクトップを実行している場合、Kubernetes は既に使用可能です。 [**設定**] ウィンドウの [ **Kubernetes** ] セクションで有効にするだけです。

![Docker Desktop で Kubernetes を有効にする](media/kubernetes/enable-kubernetes-docker-desktop-v2.png)

Linux でローカル Kubernetes クラスターを実行する場合は、Linux ディストリビューションで[スナップ](https://snapcraft.io/)がサポートされている場合は[Minikube](https://github.com/kubernetes/minikube)または[MicroK8s](https://microk8s.io/)を検討してください。

クラスターが実行されていて、アクセス可能であることを確認するには、次のコマンドを実行し `kubectl version` ます。

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:50:19Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:41:49Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"linux/amd64"}
```

この例で `kubectl` は、CLI と Kubernetes サーバーの両方でバージョン1.14.6 が実行されています。 の各バージョン `kubectl` は、サーバーの以前のバージョンと次のバージョンをサポートすることを想定しているため、 `kubectl` 1.14 はサーバーバージョン1.13 と1.15 でも動作します。

## <a name="run-services-on-kubernetes"></a>Kubernetes でサービスを実行する

サンプルアプリケーションには、 `kube` 3 つの YAML ファイルを含むディレクトリがあります。 ファイルは、 `namespace.yml` カスタム名前空間を宣言 `stocks` します。 `stockdata.yml`ファイルは grpc アプリケーションのデプロイとサービスを宣言し、 `stockweb.yml` ファイルは grpc サービスを使用する ASP.NET CORE 5.0 MVC web アプリケーションのデプロイとサービスを宣言します。

でファイルを使用するには `YAML` `kubectl` 、次のコマンドを実行し `apply -f` ます。

```console
kubectl apply -f object.yml
```

コマンドは、 `apply` YAML ファイルの有効性を確認し、API から受信したすべてのエラーを表示しますが、ファイルで宣言されているすべてのオブジェクトが作成されるまで待機しません。これは、この手順に時間がかかることがあるためです。 コマンドと関連するオブジェクトの種類を使用して、 `kubectl get` クラスターでのオブジェクトの作成を確認します。

### <a name="the-namespace-declaration"></a>名前空間の宣言

名前空間の宣言は単純であり、を割り当てるだけで済み `name` ます。

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

を使用して `kubectl` ファイルを適用 `namespace.yml` し、名前空間が正常に作成されたことを確認します。

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a>StockData アプリケーション

`stockdata.yml`ファイルは、配置とサービスという2つのオブジェクトを宣言します。

#### <a name="the-stockdata-deployment"></a>StockData のデプロイ

YAML ファイルの配置部分には、 `spec` 必要なレプリカの数を含む、デプロイ自体のが用意されています。また、は、 `template` 配置によって作成および管理される Pod オブジェクトのを提供します。 配置オブジェクトは `apps` `apiVersion` 、メインの Kubernetes api ではなく、で指定された api によって管理されることに注意してください。

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 1
  template:
    metadata:
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

`spec.selector`プロパティは、実行中のポッドをデプロイと照合するために使用されます。 ポッドのプロパティがプロパティと一致して `metadata.labels` いる必要があります。指定しないと、 `matchLabels` API 呼び出しは失敗します。

セクションでは、 `template.spec` 実行するコンテナーを宣言します。 Docker Desktop によって提供されるものなど、ローカル Kubernetes クラスターを使用している場合は、バージョンタグがある限り、ローカルでビルドされたイメージを指定できます。

> [!IMPORTANT]
> 既定では、Kubernetes は常にを確認し、新しいイメージをプルしようとします。 既知のリポジトリにイメージが見つからない場合、ポッドの作成は失敗します。 ローカルイメージを操作するには、 `imagePullPolicy` をに設定し `Never` ます。

プロパティは、 `ports` ポッドで公開するコンテナーポートを指定します。 `stockservice`イメージは標準の HTTP ポートでサービスを実行するので、ポート80が公開されます。

セクションでは、 `resources` ポッド内で実行されているコンテナーにリソースの制限を適用します。 これは、個々のポッドがノード上の使用可能な CPU またはメモリをすべて消費しないようにするため、この方法が適しています。

> [!NOTE]
> ASP.NET Core 5.0 は、リソースが制限されたコンテナーで実行するように最適化およびチューニングされています。 Docker イメージは、環境変数を設定して、 `dotnet/core/aspnet` `dotnet` それがコンテナー内にあることをランタイムに通知します。

#### <a name="the-stockdata-service"></a>StockData サービス

YAML ファイルのサービス部分では、クラスター内のポッドへのアクセスを提供するサービスを宣言します。

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

サービスは、 `spec` プロパティを使用し `selector` て実行を照合し `Pods` ます。この例では、ラベルを持つポッドを探し `run: stockdata` ます。 一致するポッドに指定されたは、 `port` 名前付きサービスによって発行されます。 名前空間で実行されている他のポッド `stocks` は、アドレスとしてを使用して、このサービスの HTTP にアクセスでき `http://stockdata` ます。 他の名前空間で実行されているポッドは、ホスト名を使用でき `http://stockdata.stocks` ます。 [ネットワークポリシー](https://kubernetes.io/docs/concepts/services-networking/network-policies/)を使用して、名前空間間サービスアクセスを制御できます。

#### <a name="deploy-the-stockdata-application"></a>StockData アプリケーションをデプロイする

を使用して `kubectl` ファイルを適用 `stockdata.yml` し、展開とサービスが作成されたことを確認します。

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a>StockWeb アプリケーション

ファイルは、 `stockweb.yml` MVC アプリケーションのデプロイとサービスを宣言します。

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a>環境変数

`env`Deployment オブジェクトのセクションでは、イメージを実行しているコンテナーに設定する環境変数を指定し `stockweb:1.0.0` ます。

**`StockData__Address`** 環境変数は、 `StockData:Address` EnvironmentVariables 構成プロバイダーによって構成設定にマップされます。 この設定では、名前の間に2つのアンダースコアを使用し、セクションを区切ります。 このアドレスは、 `stockdata` 同じ Kubernetes 名前空間で実行されているサービスのサービス名を使用します。

**`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** 環境変数は、 <xref:System.AppContext> の暗号化されていない HTTP/2 接続を有効にするスイッチを設定し <xref:System.Net.Http.HttpClient> ます。 この環境変数は、次に示すように、コードでスイッチを設定するのと同じことを行います。

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

スイッチに環境変数を使用すると、アプリケーションが実行されているコンテキストに応じてコンテキストを簡単に変更できます。

#### <a name="service-types"></a>サービスの種類

`type: NodePort`プロパティは、クラスターの外部から web アプリケーションにアクセスできるようにするために使用されます。 このプロパティの種類を Kubernetes と、サービスのポート80がクラスターの外部ネットワークソケットの任意のポートに発行されます。 割り当てられたポートは、コマンドを使用して見つけることができ `kubectl get service` ます。

`stockdata`クラスターの外部からサービスにアクセスできないようにするため、既定の種類のを使用し `ClusterIP` ます。

実稼働システムでは、通常、統合されたロードバランサーを使用して、パブリックアプリケーションを外部のコンシューマーに公開します。 この方法で公開されるサービスでは、型を使用する必要があり `LoadBalancer` ます。

サービスの種類の詳細については、 [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) のドキュメントを参照してください。

#### <a name="deploy-the-stockweb-application"></a>StockWeb アプリケーションをデプロイする

を使用して `kubectl` ファイルを適用 `stockweb.yml` し、展開とサービスが作成されたことを確認します。

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

コマンドの出力は、 `get service` HTTP ポートが `32564` 外部ネットワーク上のポートに発行されていることを示しています。 Docker Desktop の場合、この IP アドレスは localhost になります。 アプリケーションにアクセスするには、を参照 `http://localhost:32564` します。

### <a name="test-the-application"></a>アプリケーションをテストする

StockWeb アプリケーションでは、単純な要求/応答サービスから取得された NASDAQ 株式の一覧が表示されます。 このデモでは、各行には、それを返したサービスインスタンスの一意の ID も表示されます。

![StockWeb スクリーンショット](media/kubernetes/stockweb-screenshot.png)

サービスのレプリカの数が増加した場合は、 `stockdata` **サーバー** の値が行ごとに変更されることが予想されますが、実際には、100のすべてのレコードが常に同じインスタンスから返されます。 数秒ごとにページを更新した場合、サーバー ID は変わりません。 なぜこのようになるのですか? ここでは2つの要素について説明します。

まず、Kubernetes Service discovery システムは、既定でラウンドロビンの負荷分散を使用します。 最初に DNS サーバーにクエリを実行すると、サービスに対して最初に一致する IP アドレスが返されます。 次に、リスト内の次の IP アドレスを返します。これは最後まで続きます。 その時点で、start にループバックします。

次に、 `HttpClient` StockWeb アプリケーションの gRPC クライアントに使用されるが [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)によって作成および管理され、このクライアントの1つのインスタンスがページへのすべての呼び出しに使用されます。 クライアントは DNS 参照を1つだけ行うため、すべての要求が同じ IP アドレスにルーティングされます。 また、はパフォーマンス上の理由でキャッシュされているため、 `HttpClientHandler` 複数の要求が同時に同じ IP アドレスを使用します。キャッシュされた DNS エントリの有効期限が切れるか、何らかの理由でハンドラーインスタンスが破棄さ *れ* ます。

その結果、既定では、gRPC サービスへの要求は、クラスター内のそのサービスのすべてのインスタンスでバランスが取れていないことになります。 コンシューマーによって使用されるインスタンスは異なりますが、要求の配布やリソースのバランスの取れた使用は保証されません。

次の章「 [サービスメッシュ](service-mesh.md)」では、この問題に対処します。

>[!div class="step-by-step"]
>[前へ](docker.md)
>[次へ](service-mesh.md)
