---
title: Wcf 開発者向けの gRPC-gRPC への WCF 双方向サービスの移行
description: さまざまな形式の WCF 双方向サービスを gRPC streaming services に移行する方法について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: 4741e5ad5c12fa358853381d4f2c286add14f8f5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938027"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a>WCF 双方向サービスを gRPC に移行する

ここでは、基本的な概念を理解しました。このセクションでは、より複雑な *ストリーミング* grpc サービスについて説明します。

Windows Communication Foundation (WCF) で双方向サービスを使用するには、複数の方法があります。 一部のサービスはクライアントによって開始され、サーバーからデータをストリーミングします。 その他の全二重サービスには、WCF ドキュメントにある従来の電卓の例のように、継続的な双方向通信が含まれる場合があります。 この章では、2つの WCF stock ティッカー実装を実行し、gRPC に移行します。1つはサーバーストリーミング RPC を使用し、もう1つは双方向ストリーミング RPC を使用します。

## <a name="server-streaming-rpc"></a>サーバーストリーミング RPC

SimpleStockPriceTicker の [サンプル SimpleStockTicker WCF ソリューション](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker)では、クライアントが株価記号の一覧を使用して接続を開始する双方向サービスがあり、サーバーは *コールバックインターフェイス* を使用して更新プログラムが使用可能になったときにそれらを送信します。 クライアントは、サーバーからの呼び出しに応答するために、そのインターフェイスを実装します。

### <a name="the-wcf-solution"></a>WCF ソリューション

WCF ソリューションは、自己ホスト型の Net.tcp サーバーとして .NET Framework 4 に実装されています。*x* コンソールアプリケーション。

#### <a name="servicecontract"></a>ServiceContract

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

サービスには、コールバックインターフェイスを使用して `ISimpleStockTickerCallback` リアルタイムでクライアントにデータを送信するため、戻り値の型のない1つのメソッドがあります。

#### <a name="the-callback-interface"></a>コールバックインターフェイス

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

これらのインターフェイスの実装と、フェイク外部依存関係を使用してテストデータを提供できます。

### <a name="grpc-streaming"></a>gRPC ストリーミング

リアルタイムデータを処理するための gRPC プロセスは、WCF プロセスとは異なります。 クライアントからサーバーへの呼び出しでは、永続的なストリームを作成できます。このストリームは、非同期的に到着するメッセージを監視できます。 違いにかかわらず、ストリームは、このデータを処理するためのより直観的な方法であり、LINQ、リアクティブストリーム、関数型プログラミングなどを重視する最新のプログラミングにおいてさらに関連性があります。

サービス定義には2つのメッセージが必要です。1つは要求用で、もう1つはストリーム用です。 サービスは、 `StockTickerUpdate` 宣言にキーワードを含むメッセージのストリームを返し `stream` `return` ます。 `Timestamp`価格変更の正確な時間を表示するには、更新プログラムにを追加することをお勧めします。

#### <a name="simple_stock_tickerproto"></a>simple_stock_ticker. proto

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.SimpleStockTickerServer.Protos";

import "google/protobuf/timestamp.proto";

package SimpleStockTickerServer;

service SimpleStockTicker {
  rpc Subscribe (SubscribeRequest) returns (stream StockTickerUpdate);
}

message SubscribeRequest {
  repeated string symbols = 1;
}

message StockTickerUpdate {
  string symbol = 1;
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-simplestockticker"></a>SimpleStockTicker を実装する

`StockPriceSubscriber` `TraderSys.StockMarket` クラスライブラリからターゲットソリューションの新しい .NET Standard クラスライブラリに3つのクラスをコピーして、WCF プロジェクトのフェイクを再利用します。 ベストプラクティスに従うには、型を追加 `Factory` してインスタンスを作成し、を `IStockPriceSubscriberFactory` ASP.NET Core 依存関係挿入サービスに登録します。

#### <a name="the-factory-implementation"></a>ファクトリ実装

```csharp
public interface IStockPriceSubscriberFactory
{
    IStockPriceSubscriber GetSubscriber(string[] symbols);
}

public class StockPriceSubscriberFactory : IStockPriceSubscriberFactory
{
    public IStockPriceSubscriber GetSubscriber(string[] symbols)
    {
        return new StockPriceSubscriber(symbols);
    }
}
```

#### <a name="register-the-factory"></a>ファクトリの登録

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

これで、このクラスを使用して gRPC を実装できるようになりました `StockTickerService` 。

#### <a name="stocktickerservicecs"></a>StockTickerService.cs

```csharp
public class StockTickerService : Protos.SimpleStockTicker.SimpleStockTickerBase
{
    private readonly IStockPriceSubscriberFactory _subscriberFactory;

    public StockTickerService(IStockPriceSubscriberFactory subscriberFactory)
    {
        _subscriberFactory = subscriberFactory;
    }

    public override async Task Subscribe(SubscribeRequest request, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
    {
        var subscriber = _subscriberFactory.GetSubscriber(request.Symbols.ToArray());

        subscriber.Update += async (sender, args) =>
            await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

        await AwaitCancellation(context.CancellationToken);
    }

    private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
    {
        try
        {
            await stream.WriteAsync(new StockTickerUpdate
            {
                Symbol = symbol,
                PriceCents = (int)(price * 100),
                Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
            });
        }
        catch (Exception e)
        {
            // Handle any errors caused by broken connection, etc.
            _logger.LogError($"Failed to write message: {e.Message}");
        }
    }

    private static Task AwaitCancellation(CancellationToken token)
    {
        var completion = new TaskCompletionSource<object>();
        token.Register(() => completion.SetResult(null));
        return completion.Task;
    }
}
```

ご覧のように、ファイル内の宣言では、 `.proto` メソッドがメッセージのストリームを返すことが示されて `StockTickerUpdate` いますが、実際にはを返し `Task` ます。 ストリームを作成するジョブは、生成されたコードと、応答ストリームを提供する gRPC ランタイムライブラリによって処理され、 `IServerStreamWriter<StockTickerUpdate>` 使用できるようになります。

接続が開いている間にサービスクラスのインスタンスが保持されている WCF 双方向サービスとは異なり、gRPC サービスは返されたタスクを使用してサービスを維持します。 接続が閉じられるまで、タスクは完了しません。

サービスは、からのを使用して、クライアントが接続を閉じたことを通知でき `CancellationToken` `ServerCallContext` ます。 単純な静的メソッドである `AwaitCancellation` は、トークンが取り消されたときに完了するタスクを作成するために使用されます。

メソッドで、を `Subscribe` 取得 `StockPriceSubscriber` し、応答ストリームに書き込むイベントハンドラーを追加します。 次に、接続が閉じられるのを待って `subscriber` から、閉じたストリームにデータを書き込むことができないようにを直ちに破棄します。

`WriteUpdateAsync`メソッドには、 `try` / `catch` ストリームにメッセージが書き込まれたときに発生する可能性のあるエラーを処理するブロックがあります。 この考慮事項は、意図的に、またはどこかの障害が原因で、任意のミリ秒で中断される可能性があるネットワーク経由の永続的な接続において重要です。

### <a name="use-stocktickerservice-from-a-client-application"></a>クライアントアプリケーションからの Stockkerservice の使用

ファイルから共有可能なクライアントクラスライブラリを作成するには、前のセクションと同じ手順に従い `.proto` ます。 このサンプルには、クライアントの使用方法を示す .NET コンソールアプリケーションが用意されています。

#### <a name="example-programcs"></a>Program.cs の例

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using var channel = GrpcChannel.ForAddress("https://localhost:5001");
        var client = new SimpleStockTicker.SimpleStockTickerClient(channel);

        var request = new SubscribeRequest();
        request.Symbols.AddRange(args);

        using var stream = client.Subscribe(request);

        var tokenSource = new CancellationTokenSource();

        var task = DisplayAsync(stream.ResponseStream, tokenSource.Token);

        WaitForExitKey();

        tokenSource.Cancel();
        await task;
    }
}
```

この場合、 `Subscribe` 生成されたクライアントのメソッドは非同期ではありません。 ストリームが作成され、そのメソッドが非同期であるため、すぐに使用できるようになり `MoveNext` ます。最初に呼び出されたときは、接続が有効になるまで完了しません。

ストリームは、非同期メソッドに渡され `DisplayAsync` ます。 アプリケーションは、ユーザーがキーを押すまで待機してから、メソッドをキャンセル `DisplayAsync` し、タスクが完了するのを待ってから終了します。

> [!NOTE]
> このコードでは、新しい C# 8 宣言構文を使用して、 `using` メソッドの終了時にストリームとチャネルを破棄し `Main` ます。 これは小さな変更ですが、インデントや空の線を減らすことができます。

#### <a name="consume-the-stream"></a>ストリームを使用する

WCF では、コールバックインターフェイスを使用して、サーバーがクライアント上でメソッドを直接呼び出すことができます。 gRPC ストリームの動作は異なります。 クライアントは、返されたストリームに対して反復処理を行い、を返すローカルメソッドから返された場合と同じように、メッセージを処理し `IEnumerable` ます。

`IAsyncStreamReader<T>`型は、のように動作 `IEnumerator<T>` します。 `MoveNext`より多くのデータがある限り true を返すメソッドと、 `Current` 最新の値を返すプロパティがあります。 唯一の違いは、メソッドが単にでは `MoveNext` なくを返すことです `Task<bool>` `bool` 。 `ReadAllAsync`拡張メソッドは、 `IAsyncEnumerable` 新しい構文で使用できる標準の C# 8 でストリームをラップし `await foreach` ます。

```csharp
static async Task DisplayAsync(IAsyncStreamReader<StockTickerUpdate> stream, CancellationToken token)
{
    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            Console.WriteLine($"{update.Symbol}: {update.Price}");
        }
    }
    catch (RpcException e) when (e.StatusCode == StatusCode.Cancelled)
    {
        return;
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Finished.");
    }
}
```

> [!TIP]
> 事後対応型のプログラミングパターンを使用する開発者にとって、この章の最後にある「 [クライアントライブラリ](client-libraries.md#iobservable) 」のセクションでは、でラップする拡張メソッドとクラスを追加する方法を示し `IAsyncStreamReader<T>` `IObservable<T>` ます。

ここでも、ネットワークエラーが発生する可能性があるため、ここで例外をキャッチしてください。これは、 <xref:System.OperationCanceledException> コードがを使用してループを中断するため、必然的にスローされるためです <xref:System.Threading.CancellationToken> 。 型には `RpcException` 、などの gRPC ランタイムエラーに関する有用な情報が多数含まれてい `StatusCode` ます。 詳細については、[第4章の「*エラー処理*](error-handling.md)」を参照してください。

## <a name="bidirectional-streaming"></a>双方向ストリーミング

WCF の全二重サービスを使用すると、非同期のリアルタイムメッセージングを双方向で実現できます。 サーバーストリーミングの例では、クライアントが要求を開始し、更新のストリームを受信します。 適切なバージョンのサービスを使用すると、クライアントは、停止して新しいサブスクリプションを作成することなく、一覧に対して株式の追加や削除を行うことができます。 この機能は、 [Fullstockticker サンプルソリューション](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)に実装されています。

`IFullStockTickerService`インターフェイスには、次の3つのメソッドがあります。

- `Subscribe` 接続を開始します。
- `AddSymbol` ウォッチするストックシンボルを追加します。
- `RemoveSymbol` ウォッチ対象のリストからシンボルを削除します。

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(IFullStockTickerCallback))]
public interface IFullStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe();

    [OperationContract(IsOneWay = true)]
    void AddSymbol(string symbol);

    [OperationContract(IsOneWay = true)]
    void RemoveSymbol(string symbol);
}
```

コールバックインターフェイスは同じままです。

このパターンを gRPC に実装するのは簡単ではありません。これは、1つはクライアントからサーバー、もう1つはサーバーからクライアントの2つのデータストリームが渡されるためです。 複数のメソッドを使用して追加と削除の操作を実装することはできませんが、1つのストリームに複数の種類のメッセージを渡すことはできません `Any` 。そのためには、 `oneof` [第3章](protobuf-any-oneof.md)で説明した型またはキーワードを使用します。

許容される特定の型のセットがある場合は、を使用 `oneof` する方が適切な方法です。 `ActionMessage`またはのいずれかを保持できるを使用し `AddSymbolRequest` `RemoveSymbolRequest` ます。

```protobuf
message ActionMessage {
  oneof action {
    AddSymbolRequest add = 1;
    RemoveSymbolRequest remove = 2;
  }
}

message AddSymbolRequest {
  string symbol = 1;
}

message RemoveSymbolRequest {
  string symbol = 1;
}
```

メッセージのストリームを受け取る双方向ストリーミングサービスを宣言し `ActionMessage` ます。

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

このサービスの実装は、前の例と似ていますが、メソッドの最初のパラメーター `Subscribe` がで、 `IAsyncStreamReader<ActionMessage>` `Add` 要求と要求を処理するために使用できるようになりました `Remove` 。

```csharp
public override async Task Subscribe(IAsyncStreamReader<ActionMessage> requestStream, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
{
    using var subscriber = _subscriberFactory.GetSubscriber();

    subscriber.Update += async (sender, args) =>
        await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

    var actionsTask = HandleActions(requestStream, subscriber, context.CancellationToken);

    _logger.LogInformation("Subscription started.");
    await AwaitCancellation(context.CancellationToken);

    try { await actionsTask; } catch { /* Ignored */ }

    _logger.LogInformation("Subscription finished.");
}

private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
{
    try
    {
        await stream.WriteAsync(new StockTickerUpdate
        {
            Symbol = symbol,
            PriceCents = (int)(price * 100),
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }
    catch (Exception e)
    {
        // Handle any errors caused by broken connection, etc.
        _logger.LogError($"Failed to write message: {e.Message}");
    }
}

private static Task AwaitCancellation(CancellationToken token)
{
    var completion = new TaskCompletionSource<object>();
    token.Register(() => completion.SetResult(null));
    return completion.Task;
}
```

GRPC が生成したクラスは、 `ActionMessage` プロパティとプロパティのいずれか1つだけを設定できることを保証し `Add` `Remove` ます。 どのような種類のメッセージが使用されている `null` かを判断するための有効な方法として、どちらを使用しているかはわかりません。 また、コード生成によって、クラスにが作成されました `enum ActionOneOfCase` `ActionMessage` 。これは次のようになります。

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

オブジェクトのプロパティを `ActionCase` `ActionMessage` ステートメントと共に使用して、 `switch` どのフィールドが設定されているかを判断できます。

```csharp
private async Task HandleActions(IAsyncStreamReader<ActionMessage> requestStream, IFullStockPriceSubscriber subscriber, CancellationToken token)
{
    await foreach (var action in requestStream.ReadAllAsync(token))
    {
        switch (action.ActionCase)
        {
            case ActionMessage.ActionOneofCase.None:
                _logger.LogWarning("No Action specified.");
                break;
            case ActionMessage.ActionOneofCase.Add:
                subscriber.Add(action.Add.Symbol);
                break;
            case ActionMessage.ActionOneofCase.Remove:
                subscriber.Remove(action.Remove.Symbol);
                break;
            default:
                _logger.LogWarning($"Unknown Action '{action.ActionCase}'.");
                break;
        }
    }
}
```

> [!TIP]
> `switch`ステートメントには、 `default` 不明な値が検出された場合に警告をログに記録するケースがあり `ActionOneOfCase` ます。 これは、 `.proto` より多くのアクションが追加された新しいバージョンのファイルをクライアントが使用していることを示す場合に便利です。 これは、を使用すること `switch` が、既知のフィールドでのテストよりも優れている理由の1つです `null` 。

### <a name="use-fullstocktickerservice-from-a-client-application"></a>クライアントアプリケーションからの FullStockTickerService の使用

この複雑なクライアントの使用方法を示す単純な .NET WPF アプリケーションがあります。 完全なアプリケーションについては、 [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)を参照してください。

クライアントは、クラスで使用されます `MainWindowViewModel` 。このクラスは、 `FullStockTicker.FullStockTickerClient` 依存関係の挿入から型のインスタンスを取得します。

```csharp
public class MainWindowViewModel : IAsyncDisposable, INotifyPropertyChanged
{
    private readonly FullStockTicker.FullStockTickerClient _client;
    private readonly AsyncDuplexStreamingCall<ActionMessage, StockTickerUpdate> _duplexStream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _responseTask;
    private string _addSymbol;

    public MainWindowViewModel(FullStockTicker.FullStockTickerClient client)
    {
        _cancellationTokenSource = new CancellationTokenSource();
        _client = client;
        _duplexStream = _client.Subscribe();
        _responseTask = HandleResponsesAsync(_cancellationTokenSource.Token);

        AddCommand = new AsyncCommand(Add, CanAdd);
    }
```

メソッドによって返されるオブジェクト `client.Subscribe()` は、gRPC ライブラリ型のインスタンスになりました。これは、 `AsyncDuplexStreamingCall<TRequest, TResponse>` `RequestStream` サーバーに要求を送信し、応答を処理するためのを提供し `ResponseStream` ます。

要求ストリームは、 `ICommand` シンボルを追加および削除するために、一部の WPF メソッドから使用されます。 各操作について、オブジェクトの関連するフィールドを設定し `ActionMessage` ます。

```csharp
private async Task Add()
{
    if (CanAdd())
    {
        await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Add = new AddSymbolRequest {Symbol = AddSymbol}});
    }
}

public async Task Remove(PriceViewModel priceViewModel)
{
    await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Remove = new RemoveSymbolRequest {Symbol = priceViewModel.Symbol}});
    Prices.Remove(priceViewModel);
}
```

> [!IMPORTANT]
> `oneof`メッセージにフィールドの値を設定すると、以前に設定されていたすべてのフィールドが自動的にクリアされます。

応答のストリームは、メソッドで処理され `async` ます。 返されるは、 `Task` ウィンドウが閉じられたときに破棄されることを保持します。

```csharp
private async Task HandleResponsesAsync(CancellationToken token)
{
    var stream = _duplexStream.ResponseStream;

    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            var price = Prices.FirstOrDefault(p => p.Symbol.Equals(update.Symbol));
            if (price == null)
            {
                price = new PriceViewModel(this) {Symbol = update.Symbol, Price = update.PriceCents / 100m};
                Prices.Add(price);
            }
            else
            {
                price.Price = update.PriceCents / 100m;
            }
        }
    }
    catch (OperationCancelledException) { }
}
```

### <a name="client-cleanup"></a>クライアントのクリーンアップ

ウィンドウが閉じられ、が `MainWindowViewModel` 破棄されると ( `Closed` のイベントから)、オブジェクトを適切に破棄することをお `MainWindow` 勧めし `AsyncDuplexStreamingCall` ます。 特に、 `CompleteAsync` `RequestStream` サーバー上のストリームを適切に閉じるには、のメソッドを呼び出す必要があります。 この例は、 `DisposeAsync` サンプルビューモデルのメソッドを示しています。

```csharp
public async ValueTask DisposeAsync()
{
    try
    {
        await _duplexStream.RequestStream.CompleteAsync().ConfigureAwait(false);
        await _responseTask.ConfigureAwait(false);
    }
    finally
    {
        _duplexStream.Dispose();
    }
}
```

要求ストリームを閉じると、サーバーは独自のリソースを適時に破棄できます。 これにより、サービスの効率とスケーラビリティが向上し、例外が回避されます。

>[!div class="step-by-step"]
>[前へ](migrate-request-reply.md)
>[次へ](streaming-versus-repeated.md)
