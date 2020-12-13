---
title: 非同期プログラミング
description: 'F # が、コア関数型プログラミングの概念から派生した言語レベルのプログラミングモデルに基づいて、非同期性のクリーンサポートを提供する方法について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 8bf8d6987187377cc1f44e77141b5d70d873f849
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366814"
---
# <a name="async-programming-in-f"></a>F での非同期プログラミング\#

非同期プログラミングは、さまざまな理由で、最新のアプリケーションに不可欠なメカニズムです。 ほとんどの開発者が直面する主なユースケースには、次の2つがあります。

- 多数の同時受信要求を処理できるサーバープロセスを提示する一方で、要求の処理中に使用されるシステムリソースを最小限に抑えながら、そのプロセスの外部のシステムまたはサービスからの入力を待機します。
- バックグラウンド作業の同時進行中に応答性の高い UI またはメインスレッドを維持する

多くの場合、バックグラウンド作業には複数のスレッドの使用が含まれますが、非同期性とマルチスレッドの概念を個別に考慮することが重要です。 実際には、個別の懸念事項であり、もう一方については意味がありません。 この記事では、個別の概念について詳しく説明します。

## <a name="asynchrony-defined"></a>定義された非同期性

前の点では、非同期性は複数のスレッドの使用状況に依存していません。もう少し説明しておくことをお勧めします。 関連することがある3つの概念がありますが、厳密に独立しています。

- 多重複数の計算が重複する時間間隔で実行される場合。
- 次数複数の計算または1つの計算の一部が同時に実行される場合。
- 非同期性メインプログラムフローとは別に1つ以上の計算を実行する場合。

これら3つは直交概念ですが、特に一緒に使用する場合は、簡単にまとめることができます。 たとえば、複数の非同期計算を並行して実行することが必要になる場合があります。 このリレーションシップは、並列処理または非同期性が互いを意味するという意味ではありません。

"非同期" という単語の etymology を検討している場合は、次の2つの部分が関係します。

- "a"、つまり "not" を意味します。
- "同期"、つまり "同時に"。

これらの2つの用語をまとめておくと、"非同期" とは "同時に実行しない" ことを意味します。 以上で作業は終了です。 この定義では、同時実行または並列処理には意味がありません。 これは実際にも当てはまります。

実際には、F # での非同期計算は、メインプログラムフローとは別に実行するようにスケジュールされています。 この独立した実行は、同時実行または並列処理を意味しません。また、計算が常にバックグラウンドで発生することも意味しません。 実際、非同期計算は、計算の性質と計算が実行されている環境に応じて、同期的に実行することもできます。

主な通じ重要は、非同期計算はメインプログラムフローに依存しないことです。 非同期計算を実行するタイミングと方法については、いくつかの保証はありますが、調整とスケジュール設定にはいくつかの方法があります。 この記事の残りの部分では、F # 非同期性の主要な概念と、F # に組み込まれている型、関数、および式の使用方法について説明します。

## <a name="core-concepts"></a>主要な概念

F # では、非同期プログラミングは次の3つの主要な概念を中心にしています。

- 型。これは、 `Async<'T>` コンポーザブルな非同期計算を表します。
- `Async`モジュール関数を使用すると、非同期処理のスケジュール設定、非同期計算の作成、および非同期結果の変換を行うことができます。
- `async { }`[コンピュテーション式](../../language-reference/computation-expressions.md)。非同期計算を構築および制御するための便利な構文を提供します。

次の例では、これら3つの概念を確認できます。

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

この例では、 `printTotalFileBytes` 関数の型は `string -> Async<unit>` です。 関数を呼び出すと、実際には非同期計算が実行されません。 代わりに、 `Async<unit>` 非同期的に実行する作業の *仕様* として機能するを返します。 `Async.AwaitTask`の本体でを呼び出し、の結果を <xref:System.IO.File.ReadAllBytesAsync%2A> 適切な型に変換します。

もう1つの重要な行は、の呼び出し `Async.RunSynchronously` です。 これは、実際に F # の非同期計算を実行する場合に呼び出す必要がある非同期モジュール開始関数の1つです。

これは、プログラミングの C#/Visual Basic スタイルとの基本的な違いです `async` 。 F # では、非同期計算は **コールドタスク** と考えることができます。 実際に実行するには、明示的に開始する必要があります。 これにはいくつかの利点があります。これにより、C# または Visual Basic よりもはるかに簡単に、非同期作業を組み合わせてシーケンス処理することができます。

## <a name="combine-asynchronous-computations"></a>非同期計算の結合

次に、計算を組み合わせることによって、前の例に基づいて構築する例を示します。

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    argv
    |> Seq.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

ご覧のように、関数には `main` さらにいくつかの要素があります。 概念的には、次のことが行われます。

1. コマンドライン引数を、 `Async<unit>` を使用した計算のシーケンスに変換 `Seq.map` します。
2. `Async<'T[]>` `printTotalFileBytes` 実行時に並列で計算をスケジュールして実行するを作成します。
3. `Async<unit>`並列計算を実行するを作成し、その結果 () を無視し `unit[]` ます。
4. 構成された計算全体をで明示的に実行し `Async.RunSynchronously` ます。この処理が完了するまでブロックします。

このプログラムが実行されると、は `printTotalFileBytes` コマンドライン引数ごとに並列で実行されます。 非同期計算はプログラムフローとは無関係に実行されるため、情報を出力して実行を終了する順序は定義されていません。 計算は並列でスケジュールされますが、実行の順序は保証されません。

## <a name="sequence-asynchronous-computations"></a>シーケンスの非同期計算

`Async<'T>`は、既に実行されているタスクではなく作業の仕様であるため、より複雑な変換を簡単に実行できます。 非同期計算のセットをシーケンス処理して、1つずつ実行する例を次に示します。

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    argv
    |> Seq.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

これは、 `printTotalFileBytes` 並列でスケジュールするのではなく、の要素の順序で実行するようにスケジュールされ `argv` ます。 後続の各操作は、前の計算の実行が完了するまではスケジュールされないため、実行中に重複が発生しないように計算がシーケンス処理されます。

## <a name="important-async-module-functions"></a>重要な非同期モジュール関数

F # で非同期コードを記述する場合は、通常、計算のスケジューリングを処理するフレームワークと対話します。 ただし、常にそうであるとは限りません。そのため、非同期処理のスケジュール設定に使用できるさまざまな関数について理解しておくことをお勧めします。

F # の非同期計算は、既に実行されている作業の表現ではなく、作業の _仕様_ であるため、開始関数を使用して明示的に開始する必要があります。 さまざまなコンテキストで役に立つ [非同期開始メソッド](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) が多数あります。 次のセクションでは、より一般的な開始関数のいくつかについて説明します。

### <a name="asyncstartchild"></a>Async. StartChild

非同期計算内で子計算を開始します。 これにより、複数の非同期計算を同時に実行できます。 子の計算では、キャンセルトークンを親計算と共有します。 親の計算が取り消された場合は、子の計算も取り消されます。

署名:

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

使う状況:

- 一度に1つずつではなく、複数の非同期計算を同時に実行するが、並列でスケジュールされていない場合。
- 子計算の有効期間を親計算の有効期間に関連付ける場合。

注意事項:

- で複数の計算を開始 `Async.StartChild` することは、並列でのスケジュール設定と同じではありません。 計算を並列でスケジュールする場合は、を使用し `Async.Parallel` ます。
- 親計算を取り消すと、開始したすべての子計算の取り消しがトリガーされます。

### <a name="asyncstartimmediate"></a>StartImmediate

非同期計算を実行し、現在のオペレーティング システムのスレッドですぐに開始します。 これは、計算中に呼び出し元のスレッドで何かを更新する必要がある場合に便利です。 たとえば、非同期計算で UI を更新する必要がある場合 (進行状況バーを更新するなど) は、を `Async.StartImmediate` 使用する必要があります。

署名:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

使う状況:

- 非同期計算の途中で、呼び出し元のスレッドで何かを更新する必要がある場合。

注意事項:

- 非同期計算のコードは、スケジュールされている任意のスレッドで実行されます。 これは、そのスレッドが UI スレッドなど、何らかの方法で重要な場合に問題になることがあります。 このような場合 `Async.StartImmediate` は、を使用するのが不適切である可能性があります。

### <a name="asyncstartastask"></a>Async.startastask

スレッド プールで計算を実行します。 <xref:System.Threading.Tasks.Task%601>計算が終了した後、対応する状態で完了するを返します (結果を生成するか、例外をスローするか、またはキャンセルします)。 キャンセルトークンが指定されていない場合は、既定のキャンセルトークンが使用されます。

署名:

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

使う状況:

- <xref:System.Threading.Tasks.Task%601>非同期計算の結果を表すためにを生成する .NET API を呼び出す必要がある場合。

注意事項:

- この呼び出しにより、追加のオブジェクトが割り当てられます `Task` 。これにより、頻繁に使用される場合にオーバーヘッドが増加する可能性があります。

### <a name="asyncparallel"></a>Async. Parallel

並列実行される一連の非同期計算をスケジュールし、指定された順序で結果の配列を生成します。 並列処理の次数は、パラメーターを指定することによって、必要に応じてチューニング/調整できます `maxDegreeOfParallelism` 。

署名:

```fsharp
computations: seq<Async<'T>> * ?maxDegreeOfParallelism: int -> Async<'T[]>
```

使用するタイミング:

- 一連の計算を同時に実行する必要があり、実行の順序に依存しない場合。
- すべてが完了するまで並列でスケジュールされた計算結果を必要としない場合。

注意事項:

- すべての計算が完了すると、結果として得られる値の配列にのみアクセスできます。
- 計算は、スケジュールが設定されると終了するたびに実行されます。 この動作は、実行順序に依存できないことを意味します。

### <a name="asyncsequential"></a>Async。シーケンシャル

渡された順序で実行される一連の非同期計算をスケジュールします。 最初の計算が実行され、その後、次のようになります。 並列では計算は実行されません。

署名:

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

使用するタイミング:

- 複数の計算を順番に実行する必要がある場合。

注意事項:

- すべての計算が完了すると、結果として得られる値の配列にのみアクセスできます。
- 計算は、この関数に渡される順序で実行されます。そのため、結果が返されるまでに時間がかかることがあります。

### <a name="asyncawaittask"></a>Async. AwaitTask

指定されたの完了を待機し、その <xref:System.Threading.Tasks.Task%601> 結果をとして返す非同期計算を返します。 `Async<'T>`

署名:

```fsharp
task: Task<'T> -> Async<'T>
```

使う状況:

- <xref:System.Threading.Tasks.Task%601>F # の非同期計算内でを返す .NET API を使用する場合。

注意事項:

- 例外は、 <xref:System.AggregateException> タスク並列ライブラリの規則に従ってラップされます。この動作は、F # の非同期で一般的に例外が表面化する方法とは異なります。

### <a name="asynccatch"></a>Async. Catch

指定されたを実行し、を返す非同期計算を作成し `Async<'T>` `Async<Choice<'T, exn>>` ます。 指定されたが正常に完了した場合は、 `Async<'T>` `Choice1Of2` 結果の値と共にが返されます。 完了前に例外がスローされた場合は、発生した `Choice2of2` 例外と共にが返されます。 多くの計算で構成され、その計算の1つが例外をスローする非同期計算で使用される場合、外側の計算は完全に停止されます。

署名:

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

使う状況:

- 例外によって失敗する可能性があり、呼び出し元でその例外を処理する必要がある非同期処理を実行する場合。

注意事項:

- 結合またはシーケンスされた非同期計算を使用する場合、その "内部" 計算の1つが例外をスローすると、外側の計算が完全に停止します。

### <a name="asyncignore"></a>Async. Ignore

指定された計算を実行する非同期計算を作成しますが、その結果は削除されます。

署名:

```fsharp
computation: Async<'T> -> Async<unit>
```

使う状況:

- 結果が不要な非同期計算がある場合。 これは、非同期で `ignore` ないコードの関数に似ています。

注意事項:

- またはを必要とする別の関数を使用するためにを使用する必要がある場合は `Async.Ignore` `Async.Start` `Async<unit>` 、結果を破棄するかどうかを検討してください。 型シグネチャに一致するように結果を破棄しないでください。

### <a name="asyncrunsynchronously"></a>Async. RunSynchronously

非同期計算を実行し、呼び出し元のスレッドでその結果を待機します。 計算によって例外が生成されるように、例外を伝達します。 この呼び出しはブロックされています。

署名:

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

使用するタイミング:

- 必要に応じて、実行可能ファイルのエントリポイントで、アプリケーション内で1回だけ使用します。
- パフォーマンスを気にせずに、他の一連の非同期操作を一度に実行する場合。

注意事項:

- を呼び出す `Async.RunSynchronously` と、実行が完了するまで呼び出し元のスレッドがブロックされます。

### <a name="asyncstart"></a>Async。開始

スレッドプールでを返す非同期計算を開始 `unit` します。 は、完了するのを待たず、または例外の結果を観察します。 で開始した入れ子になった計算 `Async.Start` は、それらを呼び出した親計算とは無関係に開始されます。有効期間は親計算に関連付けられていません。 親計算が取り消された場合、子計算は取り消されません。

署名:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

次の場合にのみ使用します。

- 非同期計算によって結果が得られないか、または処理が必要ありません。
- 非同期計算がいつ完了するかを知る必要はありません。
- 非同期計算を実行するスレッドを気にする必要はありません。
- 実行の結果として発生した例外を認識したりレポートしたりする必要はありません。

注意事項:

- で開始された計算によって発生した例外 `Async.Start` は、呼び出し元に反映されません。 呼び出し履歴は完全にアンワインドされます。
- で開始された作業 (を呼び出した場合など `printfn` ) で `Async.Start` は、プログラムの実行のメインスレッドで効果が発生しません。

## <a name="interoperate-with-net"></a>.NET との相互運用

[Async/await](../../../standard/async.md)スタイルの非同期プログラミングを使用する .net ライブラリまたは C# のコードベースを使用する場合があります。 C# およびほとんどの .NET ライブラリでは、との型は、で <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> はなく、の中核となる抽象化として使用されるため `Async<'T>` 、これら2つの方法の間の境界を非同期性に越える必要があります。

### <a name="how-to-work-with-net-async-and-taskt"></a>.NET async およびを使用する方法 `Task<T>`

を使用する .NET 非同期ライブラリおよびコードベースの操作 <xref:System.Threading.Tasks.Task%601> (つまり、戻り値を持つ非同期計算) は簡単で、F # を使用した組み込みのサポートがあります。

関数を使用すると、 `Async.AwaitTask` .net の非同期計算を待機できます。

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

関数を使用すると、 `Async.StartAsTask` 非同期計算を .net 呼び出し元に渡すことができます。

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>.NET async およびを使用する方法 `Task`

(つまり、値を返さない .NET 非同期計算) を使用する Api を操作するには、を <xref:System.Threading.Tasks.Task> に変換する関数を追加する必要があり `Async<'T>` <xref:System.Threading.Tasks.Task> ます。

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

`Async.AwaitTask`を入力として受け取るが既に存在し <xref:System.Threading.Tasks.Task> ます。 これと以前に定義された関数を使用すると、 `startTaskFromAsyncUnit` <xref:System.Threading.Tasks.Task> F # の非同期計算から型を開始および待機できます。

## <a name="relationship-to-multi-threading"></a>マルチスレッドとの関係

この記事ではスレッド処理について説明していますが、次の2つの重要な点に注意してください。

1. 現在のスレッドで明示的に開始されている場合を除き、非同期計算とスレッド間の関係はありません。
1. F # での非同期プログラミングは、マルチスレッドの抽象的なものではありません。

たとえば、作業の性質に応じて、実際には、呼び出し元のスレッドで計算が実行されます。 また、計算では、スレッド間の "ジャンプ" によって、"待機中" の期間 (ネットワーク呼び出しが転送中の場合など) の間に有用な作業を行うために、スレッド間を "移動" できます。

F # では、現在のスレッドで (または現在のスレッドではなく) 非同期計算を開始する機能が提供されますが、非同期性は通常、特定のスレッド処理方法に関連付けられていません。

## <a name="see-also"></a>関連項目

- [F # の非同期プログラミングモデル](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet .com の F # 非同期ガイド](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [楽しいと利益の非同期プログラミングガイドの F #](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [C# および F # での Async: C での非同期の課題#](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
