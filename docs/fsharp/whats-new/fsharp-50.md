---
title: 'F # 5.0 の新機能-F # ガイド'
description: 'F # 5.0 で利用可能な新機能の概要を説明します。'
ms.date: 11/06/2020
ms.openlocfilehash: 0c4c9f42c63a1dc8c90213c43edbadd4061c132d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445842"
---
# <a name="whats-new-in-f-50"></a>F # 5.0 の新機能

F # 5.0 では、F # 言語と F# インタラクティブにいくつかの機能強化が加えられています。 **.Net 5** でリリースされます。

## <a name="get-started"></a>作業開始

F # 5.0 は、すべての .NET Core ディストリビューションと Visual Studio ツールで使用できます。 詳細については、「 [F # の使用を開始](../get-started/index.md) する」を参照してください。

## <a name="package-references-in-f-scripts"></a>F # スクリプトでのパッケージ参照

F # 5 では、構文を使用して F # スクリプトにパッケージ参照がサポートさ `#r "nuget:..."` れます。 たとえば、次のパッケージ参照を考えてみます。

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn "%s" (JsonConvert.SerializeObject o)
```

次のように、パッケージの名前の後に明示的なバージョンを指定することもできます。

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

パッケージ参照は、ML.NET などのネイティブ依存関係を含むパッケージをサポートします。

パッケージ参照は、依存するを参照するための特別な要件を持つパッケージもサポート `.dll` します。 たとえば、ユーザーが F# インタラクティブで参照される前に、その依存が先に参照されていることをユーザーが手動で確認するように要求するために使用される [Fparsec](https://www.nuget.org/packages/FParsec/) パッケージなど `FParsecCS.dll` `FParsec.dll` です。 これは不要になったため、次のようにしてパッケージを参照できます。

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn "Success: %A" result
    | Failure(errorMsg, _, _) -> printfn "Failure: %s" errorMsg

test pfloat "1.234"
```

パッケージ参照の詳細については、 [F# インタラクティブ](../tutorials/fsharp-interactive/index.md) チュートリアルを参照してください。

## <a name="string-interpolation"></a>文字列補間

F # の挿入文字列は、C# または JavaScript の挿入文字列に似ています。つまり、文字列リテラル内の "穴" にコードを記述することができます。 基本的な例を次に示します。

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

ただし、F # の補間文字列では、関数と同様に、型指定された補間を使用して、 `sprintf` 補間されたコンテキスト内の式が特定の型に準拠するようにすることもできます。 同じ書式指定子を使用します。

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

前の型指定された補間の例では、で補間が型である必要がありますが、では補間がである必要があり `%s` `string` `%d` `integer` ます。

また、任意の F # 式 (または式) を補間コンテキストの側に配置することもできます。 次のように、より複雑な式を記述することもできます。

```fsharp
let str =
    $"""The result of squaring each odd item in {[1..10]} is:
{
    let square x = x * x
    let isOdd x = x % 2 <> 0
    let oddSquares xs =
        xs
        |> List.filter isOdd
        |> List.map square
    oddSquares [1..10]
}
"""
```

ただし、これはあまり実践されていません。

## <a name="support-for-nameof"></a>のためのサポート

F # 5 では演算子がサポートされてい `nameof` ます。この演算子は、で使用されているシンボルを解決し、f # ソースでその名前を生成します。 これは、ログ記録などのさまざまなシナリオで役立ち、ソースコードの変更に対するログ記録を保護します。

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) (sprintf "Value passed in was %d." month)

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

最後の行は例外をスローし、"month" はエラーメッセージに表示されます。

ほぼすべての F # コンストラクトの名前を取得できます。

```fsharp
module M =
    let f x = nameof x

printfn "%s" (M.f 12)
printfn "%s" (nameof M)
printfn "%s" (nameof M.f)
```

最後の3つの追加は、演算子のしくみに対する変更です。 `nameof<'type-parameter>` ジェネリック型パラメーターのフォームの追加と、 `nameof` パターン一致式のパターンとしての使用が可能です。

演算子の名前を取得すると、そのソース文字列が返されます。 コンパイル済みのフォームが必要な場合は、演算子のコンパイルされた名前を使用します。

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

型パラメーターの名前を取得するには、次のように若干異なる構文が必要です。

```fsharp

type C<'TType> =
    member _.TypeName = nameof<'TType>
```

これは、 `typeof<'T>` 演算子および演算子に似てい `typedefof<'T>` ます。

F # 5 では、 `nameof` 式で使用できるパターンのサポートも追加されてい `match` ます。

```fsharp
[<Struct; IsByRefLike>]
type RecordedEvent = { EventType: string; Data: ReadOnlySpan<byte> }

type MyEvent =
    | AData of int
    | BData of string

let deserialize (e: RecordedEvent) : MyEvent =
    match e.EventType with
    | nameof AData -> AData (JsonSerializer.Deserialize<int> e.Data)
    | nameof BData -> BData (JsonSerializer.Deserialize<string> e.Data)
    | t -> failwithf "Invalid EventType: %s" t
```

上記のコードでは、match 式の文字列リテラルではなく、' 文字列 ' を使用しています。

## <a name="open-type-declarations"></a>オープン型の宣言

F # 5 では、オープン型の宣言のサポートも追加されています。 オープン型の宣言は、C# で静的クラスを開くのと似ています。ただし、F # のセマンティクスに適合するように、構文や動作が少し異なります。

オープン型の宣言では、 `open` 任意の型を使用して、静的な内容をその中に公開できます。 さらに、 `open` F # で定義された共用体とレコードを使用して、その内容を公開できます。 たとえば、モジュールで共用体が定義されていて、そのケースにアクセスするが、モジュール全体を開かないようにする場合に便利です。

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

C# とは異なり、 `open type` 同じ名前を持つメンバーを公開する2つの型がある場合、最後の型のメンバーは、 `open` 他の名前をシャドウします。 これは、既に存在するシャドウ処理に関する F # のセマンティクスと一致します。

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a>組み込みデータ型のスライス動作の一貫性

組み込み `FSharp.Core` データ型 (配列、リスト、文字列、2d 配列、3d 配列、4d 配列) を、F # 5 より前の一貫性がないようにスライスする動作。 一部のエッジケースの動作で例外がスローされましたが、何も発生しませんでした。 F # 5 では、すべての組み込み型で、生成できないスライスの空のスライスが返されるようになりました。

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

// Before: would return empty list
// F# 5: same
let emptyList = l.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty array
let emptyArray = a.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty string
let emptyString = s.[-2..(-1)]
```

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a>Fsharp.core の3D および4D 配列の固定インデックススライス

F # 5.0 では、組み込みの3D および4D 配列型の固定インデックスを使用したスライスのサポートが提供されます。

これを説明するために、次の3D 配列について考えてみます。

*z = 0*
|x\y|0|1|
|---|-|-|
|**0**|0|1|
|**1**|2|3|

*z = 1*
|x\y|0|1|
|---|-|-|
|**0**|4|5|
|**1**|6|7|

配列からスライスを抽出する場合はどうすればよい `[| 4; 5 |]` でしょうか。 これは非常に単純です。

```fsharp
// First, create a 3D array to slice

let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

## <a name="applicative-computation-expressions"></a>アプリケーションの計算式

[コンピュテーション式 (CEs)](../language-reference/computation-expressions.md) は、"コンテキスト計算" をモデル化するために現在使用されています。または、関数型プログラミングのわかりやすい用語である monadic の計算に使用されています。

F # 5 では、別の計算モデルを提供するアプリケーションアプリケーションが導入されています。 アプリケーションを使用すると、すべての計算が独立しており、結果が最終的に蓄積されるため、より効率的な計算を行うことができます。 計算が相互に独立している場合は、それらも簡単に並列化できます。これにより、CE の作成者はより効率的なライブラリを記述できるようになります。 ただし、この特典には制限がありますが、以前に計算された値に依存する計算は使用できません。

次の例は、型の基本的なアプリケーションを示して `Result` います。

```fsharp
// First, define a 'zip' function
module Result =
    let zip x1 x2 =
        match x1,x2 with
        | Ok x1res, Ok x2res -> Ok (x1res, x2res)
        | Error e, _ -> Error e
        | _, Error e -> Error e

// Next, define a builder with 'MergeSources' and 'BindReturn'
type ResultBuilder() =
    member _.MergeSources(t1: Result<'T,'U>, t2: Result<'T1,'U>) = Result.zip t1 t2
    member _.BindReturn(x: Result<'T,'U>, f) = Result.map f x

let result = ResultBuilder()

let run r1 r2 r3 =
    // And here is our applicative!
    let res1: Result<int, string> =
        result {
            let! a = r1
            and! b = r2
            and! c = r3
            return a + b - c
        }

    match res1 with
    | Ok x -> printfn "%s is: %d" (nameof res1) x
    | Error e -> printfn "%s is: %s" (nameof res1) e

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

現在ライブラリで CEs を公開しているライブラリの作成者は、注意する必要がある追加の考慮事項がいくつかあります。

## <a name="interfaces-can-be-implemeneted-at-different-generic-instantiations"></a>インターフェイスは、異なる汎用インスタンス化で implemeneted ことができます。

これで、異なる汎用インスタンス化で同じインターフェイスを実装できるようになりました。

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="default-interface-member-consumption"></a>既定のインターフェイスメンバーの消費

F # 5 では、 [既定の実装でインターフェイス](../../csharp/tutorials/default-interface-methods-versions.md)を使用できます。

次のように、C# で定義されているインターフェイスについて考えてみましょう。

```csharp
using System;

namespace CSharp
{
    public interface MyDimasd
    {
        public int Z => 0;
    }
}
```

これは、インターフェイスを実装する標準の方法のいずれかを使用して F # で使用できます。

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn "DIM from C#: %d" md.Z

// You can also implement it via an object expression
let md' = { new MyDim }
printfn "DIM from C# but via Object Expression: %d" md'.Z
```

これにより、ユーザーが既定の実装を使用できることが期待される場合に、最新の c# で記述された C# コードと .NET コンポーネントを安全に利用できます。

## <a name="simplified-interop-with-nullable-value-types"></a>単純化と null 許容の値型との相互運用

[Null 許容型 (値) 型](https://docs.microsoft.com/dotnet/api/system.nullable-1) (以前は Null 許容型と呼ばれます) は F # でサポートされていますが、通常 `Nullable` は、値を渡すたびにまたはラッパーを構築する必要があるため、これらの型を操作するのはかなり困難でした `Nullable<SomeType>` 。 これで、 `Nullable<ThatValueType>` ターゲットの型がと一致する場合、コンパイラは値型をに暗黙的に変換します。 現在、次のコードを使用できます。

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

## <a name="preview-reverse-indexes"></a>プレビュー: インデックスの反転

F # 5 では、逆引きインデックスを許可するためのプレビューも導入されています。 構文は `^idx` です。 リストの末尾から要素1の値を指定する方法を次に示します。

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

また、独自の型の逆インデックスを定義することもできます。 これを行うには、次のメソッドを実装する必要があります。

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

型の例を次に示し `Span<'T>` ます。

```fsharp
open System

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

    member sp.GetReverseIndex(_, offset: int) =
        sp.Length - offset

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let run () =
    let sp = [| 1; 2; 3; 4; 5 |].AsSpan()

    // Pre-# 5.0 slicing on a Span<'T>
    printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..3] // [|1; 2; 3|]
    printSpan sp.[1..3] // |2; 3|]

    // Same slices, but only using from-the-end index
    printSpan sp.[..^0] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..^2] // [|1; 2; 3|]
    printSpan sp.[^4..^2] // [|2; 3|]

run() // Prints the same thing twice
```

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a>プレビュー: コンピュテーション式におけるカスタムキーワードのオーバーロード

コンピュテーション式は、ライブラリおよびフレームワークの作成者にとって強力な機能です。 よく知られているメンバーを定義し、作業中のドメインの DSL を形成することで、コンポーネントの表現力を大幅に向上させることができます。

F # 5 では、コンピュテーション式でカスタム操作をオーバーロードするためのプレビューサポートを追加します。 これにより、次のコードを書き込まれるして使用できるようになります。

```fsharp
open System

type InputKind =
    | Text of placeholder:string option
    | Password of placeholder: string option

type InputOptions =
  { Label: string option
    Kind : InputKind
    Validators : (string -> bool) array }

type InputBuilder() =
    member t.Yield(_) =
      { Label = None
        Kind = Text None
        Validators = [||] }

    [<CustomOperation("text")>]
    member this.Text(io, ?placeholder) =
        { io with Kind = Text placeholder }

    [<CustomOperation("password")>]
    member this.Password(io, ?placeholder) =
        { io with Kind = Password placeholder }

    [<CustomOperation("label")>]
    member this.Label(io, label) =
        { io with Label = Some label }

    [<CustomOperation("with_validators")>]
    member this.Validators(io, [<ParamArray>] validators) =
        { io with Validators = validators }

let input = InputBuilder()

let name =
    input {
    label "Name"
    text
    with_validators
        (String.IsNullOrWhiteSpace >> not)
    }

let email =
    input {
    label "Email"
    text "Your email"
    with_validators
        (String.IsNullOrWhiteSpace >> not)
        (fun s -> s.Contains "@")
    }

let password =
    input {
    label "Password"
    password "Must contains at least 6 characters, one number and one uppercase"
    with_validators
        (String.exists Char.IsUpper)
        (String.exists Char.IsDigit)
        (fun s -> s.Length >= 6)
    }
```

この変更の前には、型をそのまま記述でき `InputBuilder` ますが、この例で使用する方法を使用することはできませんでした。 オーバーロード、省略可能なパラメーター、および現在の `System.ParamArray` 型は許可されているため、期待どおりに機能するだけです。
