---
title: F# とは
description: 'F # プログラミング言語の概要と F # プログラミングについて説明します。 豊富なデータ型、関数、およびそれらがどのように組み合わされているかについて説明します。'
ms.date: 08/03/2018
ms.openlocfilehash: a6bad3e1db63c3fe948b5916925d5eb24a18a41c
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739478"
---
# <a name="what-is-f"></a>F とは\#

F # は、適切で保守が容易なコードを簡単に記述できるようにする関数型プログラミング言語です。

F # プログラミングでは、主に型の推論と一般化が自動的に行われる型と関数の定義が必要です。 これにより、プログラミングの詳細ではなく、問題のドメインにとどまり、そのデータを操作することができます。

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name = $"Hello, {name}! Isn't F# great?"

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn $"{greeting}")

    0
```

F # には、次のようなさまざまな機能があります。

* 簡易構文
* 既定で変更不可
* 型の推論と自動汎化
* ファーストクラス関数
* 強力なデータ型
* パターン マッチング
* 非同期プログラミング

すべての機能のセットについては、「 [F # 言語リファレンス](./language-reference/index.md)」で説明されています。

## <a name="rich-data-types"></a>豊富なデータ型

[レコード](./language-reference/records.md)や[判別共用体](./language-reference/discriminated-unions.md)などのデータ型を使用すると、複雑なデータとドメインを表すことができます。

```fsharp
// Group data with Records
type SuccessfulWithdrawal =
    { Amount: decimal
      Balance: decimal }

type FailedWithdrawal =
    { Amount: decimal
      Balance: decimal
      IsOverdraft: bool }

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

F # のレコードと判別共用体は、既定では非 null、不変、および比較可能であるため、非常に簡単に使用できます。

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>関数とパターンマッチングでの強制的な正確性

F # の関数は、簡単に宣言でき、非常に強力です。 [パターンマッチング](./language-reference/pattern-matching.md)と組み合わせると、コンパイラによって正確性が強制される動作を定義できます。

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f{s.Amount}"
    | InsufficientFunds f -> printfn "Failed: balance is %f{f.Balance}"
    | CardExpired d -> printfn "Failed: card expired on {d}"
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

F # 関数もファーストクラスであり、パラメーターとして渡し、他の関数から返すことができます。

## <a name="functions-to-define-operations-on-objects"></a>オブジェクトに対する操作を定義する関数

F # では、オブジェクトが完全にサポートされています。これは、データと機能をブレンドする必要がある場合に便利なデータ型です。 F # 関数は、オブジェクトの操作に使用されます。

```fsharp
type Set<'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

F # では、オブジェクト指向のコードを記述するのではなく、多くの場合、オブジェクトを操作する関数の別のデータ型として扱うコードを記述します。 [ジェネリックインターフェイス](./language-reference/interfaces.md)、[オブジェクト式](./language-reference/object-expressions.md)、[メンバー](./language-reference/members/index.md)の慎重な使用などの機能は、大きな F # プログラムでよく見られます。

## <a name="next-steps"></a>次のステップ

より大きな F # 機能セットの詳細については、 [f # ツアー](tour.md)をご覧ください。
