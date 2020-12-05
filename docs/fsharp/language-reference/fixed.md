---
title: Fixed キーワード
description: "F # の ' fixed ' キーワードを使用してコレクションを防止するために、ローカルのをスタックに \"固定\" する方法について説明します。"
ms.date: 08/15/2020
ms.openlocfilehash: b4b0d1ae101d5f7b65bff80fa070c9fd54de8d66
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740355"
---
# <a name="the-fixed-keyword"></a>Fixed キーワード

`fixed`キーワードを使用すると、ローカルのをスタックに "固定" し、ガベージコレクション中に収集または移動できないようにすることができます。  これは、低レベルのプログラミングシナリオに使用されます。

## <a name="syntax"></a>構文

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Remarks

これにより、式の構文が拡張され、ポインターを抽出して、ガベージコレクション中に収集または移動できない名前にバインドできるようになります。  

キーワードを使用して式からのポインターが固定されている場合は、キーワードを使用して `fixed` 識別子にバインドされ `use` ます。  このセマンティクスは、キーワードを使用したリソース管理に似てい `use` ます。  ポインターはスコープ内にある間は固定され、スコープ外になると修正されなくなります。  `fixed` は、バインドのコンテキストの外部では使用できません `use` 。  ポインターは、を使用して名前にバインドする必要があり `use` ます。

`fixed`は、関数またはメソッドの式の中で使用する必要があります。  スクリプトレベルまたはモジュールレベルのスコープでは使用できません。

すべてのポインターコードと同様に、これは安全でない機能であり、使用すると警告が出力されます。

## <a name="example"></a>例

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn $"pnt before - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn $"pnt after - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>関連項目

- [モジュール](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
