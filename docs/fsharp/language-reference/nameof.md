---
title: Nameof
description: ソースコード内の任意のシンボルの名前を生成できるメタプログラミング機能である、参照元の演算子について説明します。
ms.date: 11/12/2020
ms.openlocfilehash: 9947d7172d1b73db5c181297ec8b1131382e1f5e
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688632"
---
# <a name="nameof"></a>Nameof

式は、source 内の `nameof` ほぼすべての F # コンストラクトのソース内の名前と一致する文字列定数を生成します。

## <a name="syntax"></a>構文

```fsharp
nameof symbol
nameof<'TGeneric>
```

## <a name="remarks"></a>Remarks

`nameof` は、渡されたシンボルを解決して、ソースコード内で宣言されたシンボルの名前を生成することによって機能します。 これは、ログ記録などのさまざまなシナリオで役立ち、ソースコードの変更に対するログ記録を保護します。

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) ($"Value passed in was %d{month}.")

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

最後の行は例外をスローし、 `"month"` エラーメッセージに表示されます。

ほぼすべての F # コンストラクトの名前を取得できます。

```fsharp
module M =
    let f x = nameof x

printfn $"{(M.f 12)]}"
printfn $"{(nameof M)}"
printfn $"{(nameof M.f)}"
```

`nameof` がファーストクラス関数ではなく、そのように使用することはできません。 つまり、このメソッドを部分的に適用することはできず、F # パイプライン演算子を使用して値をパイプすることはできません。

## <a name="nameof-on-operators"></a>演算子の場合

F # の演算子は、演算子テキスト自体、またはコンパイルされたフォームを表す記号として2つの方法で使用できます。 `nameof` オペレーターは、ソースで宣言されている演算子の名前を生成します。 コンパイルされた名前を取得するには、ソースのコンパイル済みの名前を使用します。

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

## <a name="nameof-on-generics"></a>ジェネリックのすべてのもの

ジェネリック型パラメーターの名前を取得することもできますが、構文は異なります。

```fsharp
let f<'a> () = nameof<'a>
f() // "a"
```

`nameof<'TGeneric>` は、呼び出しサイトで置き換えられた型の名前ではなく、ソースで定義されているシンボルの名前を受け取ります。

構文が異なる理由は、やなどの他の F # 組み込み演算子と一致させることです `typeof<>` `typedefof<>` 。 これにより、ジェネリック型に作用する演算子と、ソース内の他のあらゆるものに対して F # の一貫性が確保されます。

## <a name="nameof-in-pattern-matching"></a>パターンマッチングのためのもの

[ `nameof` パターン](pattern-matching.md#nameof-pattern)を使用すると、 `nameof` パターンマッチ式で次のようにを使用できます。

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```
