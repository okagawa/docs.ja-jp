---
title: GRPC クライアントライブラリの作成-WCF 開発者向け gRPC
description: GRPC サービス用の共有クライアントライブラリ/パッケージについて説明します。
ms.date: 12/15/2020
ms.openlocfilehash: b1233bb40a5fa2119a325be2657b500a4c626c18
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938430"
---
# <a name="create-grpc-client-libraries"></a>GRPC クライアントライブラリを作成する

GRPC アプリケーション用のクライアントライブラリを配布する必要はありません。 組織内にファイルの共有ライブラリを作成することができ `.proto` ます。また、他のチームはこれらのファイルを使用して、独自のプロジェクトでクライアントコードを生成できます。 ただし、プライベート NuGet リポジトリがあり、他の多くのチームが .NET を使用している場合は、サービスプロジェクトの一部としてクライアント NuGet パッケージを作成して発行することができます。 この方法を使用すると、サービスを共有して昇格させることができます。

クライアントライブラリを配布する利点の1つは、生成された gRPC および Protobuf クラスを、便利な "便利な" メソッドとプロパティを使用して拡張できることです。 クライアントコードでは、サーバーと同様に、すべてのクラスがとして宣言されている `partial` ため、生成されたコードを編集しなくても、それらを拡張できます。 この動作は、コンストラクター、メソッド、および計算されるプロパティを基本的な型に簡単に追加できることを意味します。

> [!CAUTION]
> カスタムコードを使用して、重要な機能を提供しないでください。 共有ライブラリを使用する .NET チームにこの重要な機能を制限するのではなく、Python や Java などの他の言語やプラットフォームを使用するチームに提供する必要はありません。

可能な限り多くのチームが gRPC サービスにアクセスできることを確認します。 この機能を実行する最善の方法は、 `.proto` 開発者が独自のクライアントを生成できるようにファイルを共有することです。 このアプローチは、さまざまなチームがさまざまなプログラミング言語やフレームワークを頻繁に使用している場合や、API に外部からアクセスできる場合に、マルチプラットフォーム環境で特に当てはまります。

## <a name="useful-extensions"></a>便利な拡張機能

.NET では、オブジェクトのストリームを処理するために一般的に使用されるインターフェイスが2つあります。 <xref:System.Collections.Generic.IEnumerable%601> と <xref:System.IObservable%601> です。 .NET Core 3.0 および C# 8.0 以降では、ストリームを <xref:System.Collections.Generic.IAsyncEnumerable%601> 非同期的に処理するためのインターフェイスと、 `await foreach` インターフェイスを使用するための構文が用意されています。 このセクションでは、これらのインターフェイスを gRPC ストリームに適用する再利用可能なコードを示します。

.NET gRPC クライアントライブラリには、 `ReadAllAsync` インターフェイスを作成するの拡張メソッドが用意されて `IAsyncStreamReader<T>` `IAsyncEnumerable<T>` います。 事後対応型プログラミングを使用する開発者の場合、インターフェイスを作成するための同等の拡張メソッドは、 `IObservable<T>` 次のセクションの例のようになります。

### <a name="iobservable"></a>IObservable

`IObservable<T>`インターフェイスは、の "リアクティブ" 逆関数です `IEnumerable<T>` 。 ストリームから項目をプルするのではなく、事後対応型のアプローチによって、ストリームをサブスクライバーにプッシュすることができます。 この動作は gRPC ストリームによく似ており、インターフェイスのインターフェイスをラップするのは簡単です `IObservable<T>` `IAsyncStreamReader<T>` 。

C# には `IAsyncEnumerable<T>` observable を操作するためのサポートが組み込まれていないため、このコードはコードよりも長くなっています。 実装クラスは手動で作成する必要があります。 ただし、これはジェネリッククラスであるため、1つの実装がすべての型で動作します。

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public GrpcStreamObservable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader;
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> この監視可能な実装により、 `Subscribe` メソッドを1回だけ呼び出すことができます。これは、複数のサブスクライバーがストリームから読み取ろうとすると混乱が生じるためです。 `Replay`Observable では、この実装で使用できるように、バッファリングと反復可能な共有を有効にする、などの演算子が[あります。](https://www.nuget.org/packages/System.Reactive.Linq)

`GrpcStreamSubscription`クラスは、の列挙体を処理し `IAsyncStreamReader` ます。

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public GrpcStreamSubscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        Debug.Assert(reader != null);
        Debug.Assert(observer != null);
        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);
        _task = Run(reader, observer, _tokenSource.Token);
    }

    private async Task Run(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                observer.OnError(e);
                _completed = true;
                return;
            }

            observer.OnNext(reader.Current);
        }

        _completed = true;
        observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

ここで必要なのは、ストリームリーダーから観測可能なを作成するための単純な拡張メソッドです。

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(this IAsyncStreamReader<T> reader) =>
            new GrpcStreamObservable<T>(reader);
    }
}
```

## <a name="summary"></a>まとめ

<xref:System.IAsyncDisposable>モデルと <xref:System.IObservable%601> モデルは、.net でのデータの非同期ストリームを処理するための適切にサポートされ、適切に記述された方法です。 gRPC ストリームは、両方のパラダイムに適しており、.NET との密接な統合と、事後対応と非同期のプログラミングスタイルを提供します。

>[!div class="step-by-step"]
>[前へ](streaming-versus-repeated.md)
>[次へ](security.md)
