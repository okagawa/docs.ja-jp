---
title: トランスポート:WSE 3.0 TCP 相互運用性
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: f799f3b6968f31472acc7752846bab34351648db
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278900"
---
# <a name="transport-wse-30-tcp-interoperability"></a>トランスポート:WSE 3.0 TCP 相互運用性
WSE 3.0 TCP 相互運用性トランスポートサンプルは、カスタム Windows 通信基盤 (WCF) トランスポートとして TCP 双方向セッションを実装する方法を示しています。 さらに、チャネル レイヤーの拡張機能を使用して、ネットワーク経由で既存の配置システムと連結する方法も示します。 次の手順は、このカスタム WCF トランスポートをビルドする方法を示しています。  
  
1. まず TCP ソケットを使用して、DIME フレームを使用する <xref:System.ServiceModel.Channels.IDuplexSessionChannel> のクライアント実装とサーバー実装を作成し、メッセージ境界を決定します。  
  
2. WSE TCP サービスに接続してクライアント <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 経由でフレーム メッセージを送信する、チャネル ファクトリを作成します。  
  
3. 受信 TCP 接続を受け入れて対応するチャネルを作成するチャネル リスナーを作成します。  
  
4. ネットワーク固有の例外が、<xref:System.ServiceModel.CommunicationException> の適切な派生クラスに標準化されていることを確認します。  
  
5. チャネル スタックにカスタム トランスポートを追加するバインド要素を追加します。 詳細については、「[バインド要素の追加]」を参照してください。  
  
## <a name="creating-iduplexsessionchannel"></a>IDuplexSessionChannel の作成  
 WSE 3.0 TCP 相互運用性トランスポートを作成するには、まず、<xref:System.ServiceModel.Channels.IDuplexSessionChannel> 上に <xref:System.Net.Sockets.Socket> の実装を作成します。 `WseTcpDuplexSessionChannel` は <xref:System.ServiceModel.Channels.ChannelBase> から派生しています。 メッセージ送信のロジックは、(1) メッセージをバイトにエンコードし、(2) それらのバイトをフレーム化してネットワーク上に送信するという、2 つの主要部分で構成されます。  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 さらに、Send() 呼び出しが IDuplexSessionChannel の順序の保証を保持し、基になるソケットに対する呼び出しが正しく同期されるように、ロックを取得します。  
  
 `WseTcpDuplexSessionChannel` は、<xref:System.ServiceModel.Channels.MessageEncoder> と byte[] を相互に変換するために、<xref:System.ServiceModel.Channels.Message> を使用します。 `WseTcpDuplexSessionChannel` はトランスポートであるため、チャネルが構成されたリモート アドレスの適用も行います。 `EncodeMessage` は、この変換ロジックをカプセル化します。  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <xref:System.ServiceModel.Channels.Message> がバイトにエンコードされたら、ネットワーク上に送信する必要があります。 これを行うには、メッセージ境界を定義するシステムが必要です。 WSE 3.0 では、フレーミング プロトコルとして[DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime)のバージョンを使用します。 `WriteData` はこのフレーム ロジックをカプセル化して、byte[] を一連の DIME レコードにラップします。  
  
 メッセージを受信するロジックは似ています。 主な複雑さは、ソケットの読み取りが要求されたバイト数より少ないバイト数を返すことができるという事実を処理することです。 メッセージを受信するには、`WseTcpDuplexSessionChannel` がネットワーク経由でないバイトを読み取って DIME フレームを復号化し、その後<xref:System.ServiceModel.Channels.MessageEncoder> を使用して byte[] を <xref:System.ServiceModel.Channels.Message> に変換します。  
  
 基本の `WseTcpDuplexSessionChannel` は、接続されたソケットを受信することを前提とします。 この基本クラスでは、ソケットのシャットダウンが処理されます。 ソケットの終了と連動する場所は、次の 3 つです。  
  
- OnAbort -- ソケットを異常終了します (強制終了)。  
  
- On[Begin]Close -- ソケットを正常に終了します (正常終了)。  
  
- セッション。出力セッションを閉じる -- アウトバウンド・データ・ストリームをシャットダウンします (半分閉じる)。  
  
## <a name="channel-factory"></a>チャネル ファクトリ  
 TCP トランスポートを記述する次の手順では、クライアント チャネルでの <xref:System.ServiceModel.Channels.IChannelFactory> の実装を作成します。  
  
- `WseTcpChannelFactory`は、><xref:System.ServiceModel.Channels.ChannelFactoryBase>\<の IDuplex セッション チャネルから派生します。 このファクトリは、`OnCreateChannel` をオーバーライドして、クライアント チャネルを作成します。  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- `ClientWseTcpDuplexSessionChannel`は、時に`WseTcpDuplexSessionChannel`TCP サーバーに接続するためのロジック`channel.Open`をベースに追加します。 まず、次のコードに示すようにホスト名を解決して IP アドレスに変換します。  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- 次のコードに示すように、ホスト名はループ内で最初に利用可能な IP アドレスに接続されます。  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- チャネル コントラクトの一部として、`SocketException` の <xref:System.ServiceModel.CommunicationException> など、ドメイン固有の任意の例外をラップします。  
  
## <a name="channel-listener"></a>チャネル リスナー  
 TCP トランスポートを記述する次の手順では、サーバー チャネルを受け入れるための <xref:System.ServiceModel.Channels.IChannelListener> の実装を作成します。  
  
- `WseTcpChannelListener`<xref:System.ServiceModel.Channels.ChannelListenerBase>は、iDuplexSessionChannel> から派生し、そのリスン ソケットの有効期間を制御するために、On[Begin]オープンと On[Begin]Close をオーバーライド\<します。 OnOpen で、IP_ANY でリッスンするソケットを作成します。 より高度な実装では、同様に IPv6 でリッスンする 2 つ目のソケットを作成できます。 そのような実装では、IP アドレスをホスト名で指定することもできます。  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 新しいソケットが受け入れられると、サーバー チャネルがこのソケットで初期化されます。 すべての入出力は既に基本クラスに実装されているので、このチャネルでソケットの初期化に対応します。  
  
## <a name="adding-a-binding-element"></a>バインド要素の追加  
 ファクトリおよびチャネルを作成したら、バインディングを使用してそれらを ServiceModel ランタイムに開示する必要があります。 バインディングは、サービス アドレスに関連する通信スタックを表すバインド要素のコレクションです。 スタックの各要素は、バインド要素によって表されます。  
  
 このサンプルでは、バインド要素は `WseTcpTransportBindingElement` で、<xref:System.ServiceModel.Channels.TransportBindingElement> から派生しています。 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> がサポートされており、次のメソッドをオーバーライドして、バインディングに関連したファクトリを作成します。  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 また、この要素には、`BindingElement` を複製したり、スキーム (wse.tcp) を返したりするためのメンバーも含まれます。  
  
## <a name="the-wse-tcp-test-console"></a>WSE TCP テスト コンソール  
 このサンプルのトランスポートを使用するテスト コードは、TestCode.cs で使用できます。 WSE `TcpSyncStockService` サンプルの設定方法を次の手順に示します。  
  
 このテスト コードでは、MTOM をエンコーディングとして使用し、`WseTcpTransport` をトランスポートとして使用するカスタム バインドを作成します。 さらに、AddressingVersion を、次のコードに示すように WSE 3.0 に準拠するように設定します。  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 テスト コードは 2 つのテストで構成されます。1 つ目のテストは、WSE 3.0 WSDL から生成されたコードを使用して型指定のあるクライアントを設定します。 2 番目のテストでは、チャネル API の上に直接メッセージを送信することで、クライアントとサーバーの両方として WCF を使用します。  
  
 このサンプルを実行すると、次の出力が予測されます。  
  
 クライアント:   
  
```console  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 サーバー:   
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
## <a name="set-up-build-and-run-the-sample"></a>サンプルのセットアップ、ビルド、および実行  
  
1. このサンプルを実行するには[、Microsoft .NET 用の Web サービス拡張機能 (WSE) 3.0](https://www.microsoft.com/download/details.aspx?id=14089)が`TcpSyncStockService`インストールされている必要があります。
  
> [!NOTE]
> WSE 3.0 は Windows Server 2008 ではサポートされていないため、この`TcpSyncStockService`サンプルをオペレーティング システムにインストールまたは実行することはできません。  
  
1. `TcpSyncStockService` サンプルをインストールしたら、次の手順を実行します。  
  
    1. を`TcpSyncStockService`開きます。 (サンプルは WSE 3.0 と共にインストールされています。 このサンプルのコードの一部ではありません)。  
  
    2. StockService プロジェクトをスタートアップ プロジェクトとして設定します。  
  
    3. StockService プロジェクトの StockService.cs を開き、`StockService` クラスの [Policy] 属性をコメント化します。 これにより、サンプルのセキュリティが無効になります。 WCF は WSE 3.0 のセキュリティで保護されたエンドポイントと相互運用できますが、このサンプルをカスタム TCP トランスポートに重点を置いておくためにセキュリティは無効になっています。  
  
    4. F5 キーを押して、`TcpSyncStockService` を開始します。 サービスが新しいコンソール ウィンドウで開始します。  
  
    5. Visual Studio で、この TCP トランスポートのサンプルを開きます。  
  
    6. TestCode.cs 内の hostname 変数の値を、`TcpSyncStockService` が実行されているコンピューター名に一致するように更新します。  
  
    7. F5 キーを押して、TCP トランスポートのサンプルを開始します。  
  
    8. TCP トランスポートのテスト クライアントが、新しいコンソールで開始します。 クライアントはサービスに株価情報を要求し、その結果がコンソール ウィンドウに表示されます。  
