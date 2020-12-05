---
title: 結果
description: 'F # の "Result" 型を使用して、エラートレラントコードを記述する方法について説明します。'
ms.date: 08/13/2020
ms.openlocfilehash: 53b1db0c9224ae032d58c06cd3c58e3dbed03f7b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740225"
---
# <a name="results"></a>結果

`Result<'T,'TFailure>`型を使用すると、構成可能なエラートレラントコードを記述できます。

## <a name="syntax"></a>構文

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a>Remarks

の組み込み連結子については、モジュールを参照してください [`Result`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-resultmodule.html) `Result` 。 型のパラメーターに変換されます。

結果の型は、 [構造体の判別共用体](discriminated-unions.md#struct-discriminated-unions)であることに注意してください。 ここでは構造的等値セマンティクスが適用されます。

この `Result` 型は、通常、monadic のエラー処理で使用されます。これは、F # コミュニティ内では、" [フロント指向" プログラミング](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) と呼ばれることがよくあります。  次の簡単な例は、この方法を示しています。

```fsharp
// Define a simple type which has fields that can be validated
type Request =
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() =
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn $"My request was valid! Name: {req.Name} Email {req.Email}"  
    | Error e -> printfn $"Error: {e}"
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn $"My request was valid! Name: {req.Name} Email {req.Email}"  
    | Error e -> printfn $"Error: {e}"
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

ご覧のように、すべてを強制的にを返すようにすると、さまざまな検証関数を連結するのは非常に簡単です `Result` 。  これにより、このような機能を、必要に応じてコンポーザブルな小さな部分に分割できます。  これには、検証のラウンドの最後に [パターン一致](pattern-matching.md)の使用を *強制* するための追加の値も含まれます。これにより、より高度なプログラムの正確性が適用されます。

## <a name="see-also"></a>こちらもご覧ください

- [判別共用体](discriminated-unions.md)
- [パターン一致](pattern-matching.md)
