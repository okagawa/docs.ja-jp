---
title: Byrefs
description: '下位レベルのプログラミングに使用される、F # の byref および byref に似た型について説明します。'
ms.date: 11/04/2019
ms.openlocfilehash: ff2c06d8940f7341d5d8b1d942be264bfac586c5
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740316"
---
# <a name="byrefs"></a>Byrefs

F # には、低レベルのプログラミングの領域を処理する2つの主要な機能領域があります。

* `byref` / `inref` / `outref` 型。マネージポインターです。 実行時に無効なプログラムをコンパイルできないように、使用方法に制限があります。
* と同様の構造体 `byref` 。同様のセマンティクスと、と同じコンパイル時の制限を持つ [構造体](structures.md) です `byref<'T>` 。 例と <xref:System.Span%601> して、があります。

## <a name="syntax"></a>Syntax

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a>Byref、inref、および outref

次の3つの形式があり `byref` ます。

* `inref<'T>`は、基になる値を読み取るためのマネージポインターです。
* `outref<'T>`。基になる値に書き込むためのマネージポインター。
* `byref<'T>`は、基になる値の読み取りと書き込みを行うためのマネージポインターです。

が必要な場合は、を `byref<'T>` 渡すことができ `inref<'T>` ます。 同様に、 `byref<'T>` が必要な場合は、を渡すことができ `outref<'T>` ます。

## <a name="using-byrefs"></a>Byref の使用

を使用するには `inref<'T>` 、次のようにポインター値を取得する必要があり `&` ます。

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn $"Now: %O{dt}"

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

またはを使用してポインターに書き込むに `outref<'T>` は、 `byref<'T>` ポインターを取得する値も設定する必要があり `mutable` ます。

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn $"Now: %O{dt}"
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

ポインターを読み取る代わりに書き込みを行うだけの場合は、の代わりにを使用することを検討してください `outref<'T>` `byref<'T>` 。

### <a name="inref-semantics"></a>Inref セマンティクス

次のコードについて考えてみます。

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

意味的には、これは次のことを意味します。

* ポインターの所有者は、 `x` それを使用して値を読み取ることしかできません。
* `struct`内の入れ子になったフィールドに対して取得されたポインターに `SomeStruct` は、型が指定され `inref<_>` ます。

次のような場合もあります。

* 他のスレッドまたは別名には、への書き込みアクセス権がないという意味はありません `x` 。
* を持つ `SomeStruct` ことによって変更できない意味はありません `x` `inref` 。

ただし **、変更** できない F # 値型の場合、 `this` ポインターはとして推論され `inref` ます。

これらの規則はすべて、ポインターの所有者 `inref` が、ポイントされているメモリの直接の内容を変更しない可能性があることを意味します。

### <a name="outref-semantics"></a>Outref セマンティクス

の目的は `outref<'T>` 、ポインターを書き込むだけであることを示すことです。 予期せずに、名前に関係なく、 `outref<'T>` 基になる値の読み取りを許可します。 これは、互換性のためのものです。 意味 `outref<'T>` 的には、とは異なり `byref<'T>` ます。

### <a name="interop-with-c"></a>C との相互運用\#

C# では `in ref` 、 `out ref` 戻り値に加えて、キーワードとキーワードがサポートされてい `ref` ます。 F # が C# の出力を解釈する方法を次の表に示します。

|C# コンストラクト|F # 推論|
|------------|---------|
|`ref` 戻り値|`outref<'T>`|
|`ref readonly` 戻り値|`inref<'T>`|
|`in ref` パラメーター|`inref<'T>`|
|`out ref` パラメーター|`outref<'T>`|

F # が出力する内容を次の表に示します。

|F # コンストラクター|出力されたコンストラクト|
|------------|-----------------|
|`inref<'T>` 引数|`[In]` 引数の属性|
|`inref<'T>` 返し|`modreq` 値の属性|
|`inref<'T>` 抽象スロットまたは実装内|`modreq` on 引数または return|
|`outref<'T>` 引数|`[Out]` 引数の属性|

### <a name="type-inference-and-overloading-rules"></a>型の推定とオーバーロードの規則

`inref<'T>`型は、次の場合に F # コンパイラによって推論されます。

1. 属性を持つ .NET パラメーターまたは戻り値の型 `IsReadOnly` 。
2. 変更可能な `this` フィールドを持たない構造体型のポインター。
3. 別のポインターから派生したメモリ位置のアドレス `inref<_>` 。

の暗黙的なアドレスを取得する場合、型の引数を `inref` 持つオーバーロードは、 `SomeType` 型の引数を持つオーバーロードに優先され `inref<SomeType>` ます。 次に例を示します。

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

どちらの場合も、取得するオーバーロードは、を `System.DateTime` 取得するオーバーロードではなく、解決され `inref<System.DateTime>` ます。

## <a name="byref-like-structs"></a>Byref に似た構造体

Trio に加えて `byref` / `inref` / `outref` 、同様のセマンティクスに従うことができる独自の構造体を定義することもでき `byref` ます。 これは、属性を使用して行い <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> ます。

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` はを意味 `Struct` しません。 両方とも型に存在する必要があります。

`byref`F # の "-like" 構造体は、スタックバインド値型です。 マネージヒープに割り当てられることはありません。 と `byref` 同様の構造体は、有効期間と非キャプチャに関する厳密なチェックセットによって適用されるため、ハイパフォーマンスプログラミングに役立ちます。 規則は次のとおりです。

* これらは、関数パラメーター、メソッドパラメーター、ローカル変数、メソッドが返す値として使用できます。
* これらは、クラスまたは通常の構造体の静的メンバーまたはインスタンスメンバーにすることはできません。
* これらは、クロージャコンストラクト ( `async` メソッドまたはラムダ式) によってキャプチャすることはできません。
* これらは、ジェネリックパラメーターとして使用することはできません。

この最後の点は、 `|>` 入力の型をパラメーター化するジェネリック関数と同様に、F # パイプラインスタイルのプログラミングに不可欠です。 この制限は、インラインであるため `|>` 、その本体で非インラインジェネリック関数を呼び出すことがないため、将来は緩和される可能性があります。

これらの規則は使用法を厳密に制限していますが、高パフォーマンスコンピューティングの約束を安全な方法で実現するために使用されます。

## <a name="byref-returns"></a>Byref の戻り値

F # 関数から Byref が返されるか、メンバーを生成して使用することができます。 を `byref` 返すメソッドを使用する場合、値は暗黙的に逆参照されます。 次に例を示します。

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn $"%d{squared}"
```

値を表す値を返すには、値を含む変数が現在のスコープよりも長く有効である必要があります。
また、byref を返すには、 `&value` (value は現在のスコープよりも長い変数です) を使用します。

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

複数のチェーン呼び出しを通じて参照を渡すなど、暗黙的な逆参照を回避するには、 `&x` ( `x` は値) を使用します。

また、戻り値に直接割り当てることもでき `byref` ます。 次のような (非常に必須の) プログラムを考えてみましょう。

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn $"Original sequence: %O{c}"

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn $"New sequence:      %O{c}"

    0 // return an integer exit code
```

出力結果は次のとおりです。

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>Byref のスコープ

バインドされた値は、その `let` 参照が定義されているスコープを超えることはできません。 たとえば、次のような場合は許可されません。

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

これにより、最適化でコンパイルするかどうかによって、異なる結果が得られるのを防ぐことができます。
