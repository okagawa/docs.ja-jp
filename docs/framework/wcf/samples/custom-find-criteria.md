---
title: カスタム検索基準
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 3bafe89f5c114106eece02c41599cf485591c1cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183857"
---
# <a name="custom-find-criteria"></a>カスタム検索基準
このサンプルでは、ロジックを使用するカスタム スコープ一致の作成方法とカスタム探索サービスの実装方法を示します。 クライアントは、カスタム スコープ一致機能を使用して、システムによって提供される WCF Discovery の検索機能を改良および拡張します。 このサンプルでは次のシナリオを扱います。  
  
1. クライアントは電卓サービスを検索します。  
  
2. 検索を絞り込むために、クライアントはカスタム スコープ一致ルールを使用する必要があります。  
  
3. このルールに従って、サービスは、エンドポイントがクライアントによって指定されたスコープのいずれかと一致した場合、クライアントに応答を送り返します。  
  
## <a name="demonstrates"></a>対象  
  
- カスタム探索サービスの作成。  
  
- アルゴリズムに基づくカスタム スコープ一致の実装  
  
## <a name="discussion"></a>ディスカッション  
 クライアントは"OR"タイプの一致基準を探しています。 サービスは、エンドポイントのスコープがクライアントによって指定されたスコープのいずれかと一致した場合、応答を送り返します。 この場合、クライアントは、次のいずれかのスコープを含む電卓サービスを検索します。  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 これを行うために、クライアントはカスタム スコープ一致を URI で渡すことで、カスタム スコープ一致を使用するようにサービスに指示します。 サービスは、カスタム スコープ一致を容易にするために、カスタム スコープ一致ルールを理解し、関連する一致ロジックを実装するカスタム探索サービスを使用する必要があります。  
  
 クライアント プロジェクトで Program.cs ファイルを開きます。 `ScopeMatchBy` オブジェクトの `FindCriteria` フィールドが特定の URI に設定されていることに注意してください。 この識別子はサービスに送信されます。 サービスがこのルールを理解できない場合、クライアントの検索要求は無視されます。  
  
 サービス プロジェクトを開きます。 カスタム探索サービスの実装には、次の 3 つのファイルを使用します。  
  
1. **AsyncResult.cs**: これは、探索メソッド`AsyncResult`で必要な の実装です。  
  
2. **CustomDiscoveryService.cs**: このファイルはカスタム探索サービスを実装します。 この実装では、<xref:System.ServiceModel.Discovery.DiscoveryService> クラスを拡張し、必要なメソッドをオーバーライドします。 <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> メソッドの実装に注意してください。 このメソッドは、ルールに基づくカスタム スコープ一致がクライアントによって指定されているかどうかをチェックします。 これはクライアントが前に指定したカスタム URI です。 カスタム規則を指定した場合は、"OR" 一致ロジックを実装するコード パスが続きます。  
  
     このカスタム ロジックでは、サービスに含まれている各エンドポイントのスコープがすべてチェックされます。 エンドポイントのスコープのいずれかがクライアントによって指定されたスコープのいずれかに一致した場合、探索サービスはクライアントに送り返す応答にそのエンドポイントを追加します。  
  
3. **CustomDiscoveryExtension.cs**: 探索サービスを実装する最後の手順は、カスタム探索サービスのこの実装をサービス ホストに接続することです。 ここで使用するヘルパー クラスは `CustomDiscoveryExtension` クラスです。 このクラスは <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> クラスを拡張します。 ユーザーは <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> メソッドをオーバーライドする必要があります。 この場合、このメソッドは、前に作成されたカスタム探索サービスのインスタンスを返します。 `PublishedEndpoints` は、<xref:System.Collections.ObjectModel.ReadOnlyCollection%601> に追加されるすべてのアプリケーション エンドポイントを含む <xref:System.ServiceModel.ServiceHost> です。 カスタム探索サービスは、これを使用して内部リストを設定します。 ユーザーは、その他のエンドポイント メタデータも追加できます。  
  
 最後に、Program.cs を開きます。 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> と `CustomDiscoveryExtension` の両方がホストに追加されていることに注意してください。 これが完了し、探索メッセージの受信に使用されるエンドポイントがホストに追加されると、アプリケーションがカスタム探索サービスを使用できるようになります。  
  
 クライアントがサービスのアドレスを知ることなくサービスを検索できることを確認します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. プロジェクトを含むソリューションを開きます。  
  
2. プロジェクトをビルドします。  
  
3. サービス アプリケーションを実行します。  
  
4. クライアント アプリケーションを実行します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
