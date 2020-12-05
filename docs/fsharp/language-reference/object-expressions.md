---
title: オブジェクト式
description: '新しい名前付きの型を作成するために必要な追加のコードとオーバーヘッドを回避する必要がある場合に、F # オブジェクト式を使用する方法について説明します。'
ms.date: 02/08/2019
ms.openlocfilehash: 8a3e40b7833b551eefb95ec62b935acd1ba7b1f9
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740303"
---
# <a name="object-expressions"></a>オブジェクト式

*オブジェクト式* は、動的に作成された、既存の基本型、インターフェイス、またはインターフェイスのセットに基づく匿名オブジェクト型の新しいインスタンスを作成する式です。

## <a name="syntax"></a>構文

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Remarks

前の構文では、 *typename* は既存のクラス型またはインターフェイス型を表します。 *型-params* オプションのジェネリック型パラメーターを記述します。 *引数* は、コンストラクターパラメーターを必要とするクラス型に対してのみ使用されます。 *メンバー定義* は、基本クラスのメソッドのオーバーライド、または基本クラスまたはインターフェイスからの抽象メソッドの実装です。

次の例は、さまざまな種類のオブジェクト式を示しています。

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn $"{obj1}"

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a>オブジェクト式の使用

新しい名前付きの型を作成するために必要な追加のコードやオーバーヘッドを回避するには、オブジェクト式を使用します。 オブジェクト式を使用してプログラムで作成される型の数を最小限に抑える場合は、コードの行数を減らし、型の不必要な急増を防ぐことができます。 特定の状況に対処するためだけに多くの型を作成するのではなく、既存の型をカスタマイズするオブジェクト式を使用するか、特定のケースに対して適切なインターフェイスの実装を提供することができます。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
