---
title: インターフェイス
description: 'F # インターフェイスが、他のクラスが実装する関連メンバーのセットを指定する方法について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 0cef2932045dae401f5aa069107815543457ca4a
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557052"
---
# <a name="interfaces"></a>インターフェイス

*インターフェイス* は、他のクラスが実装する関連メンバーのセットを指定します。

## <a name="syntax"></a>構文

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>解説

インターフェイス宣言は、メンバーが実装されていないことを除いて、クラス宣言に似ています。 代わりに、キーワードによって示されているように、すべてのメンバーが抽象型に `abstract` なります。 抽象メソッドにメソッド本体を指定することはできません。 ただし、キーワードと共にメンバーの別の定義をメソッドとして含めることで、既定の実装を提供することもでき `default` ます。 これは、他の .NET 言語で基底クラスの仮想メソッドを作成することと同じです。 このような仮想メソッドは、インターフェイスを実装するクラスでオーバーライドできます。

インターフェイスの既定のアクセシビリティは `public` です。

必要に応じて、通常の F # 構文を使用して、各メソッドパラメーターに名前を付けることができます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

上の例では、メソッドには、 `ISprintable` `Print` という名前の型の1つのパラメーターがあり `string` `format` ます。

インターフェイスを実装するには、オブジェクト式を使用する方法とクラス型を使用する方法の2つの方法があります。 どちらの場合も、クラス型またはオブジェクト式は、インターフェイスの抽象メソッドにメソッド本体を提供します。 実装は、インターフェイスを実装する各型に固有です。 したがって、異なる型のインターフェイスメソッドは相互に異なる場合があります。

`interface` `end` 簡易構文を使用する場合、定義の開始と終了をマークするキーワードとは省略可能です。 これらのキーワードを使用しない場合、コンパイラは、使用するコンストラクトを分析することで、型がクラスであるかインターフェイスであるかを推論しようとします。 メンバーを定義する場合、または他のクラス構文を使用する場合、型はクラスとして解釈されます。

.NET のコーディングスタイルでは、すべてのインターフェイスを大文字で開始し `I` ます。

F # スタイルとの2つの方法で、複数のパラメーターを指定できます。NET スタイル。 どちらも .NET コンシューマーに対して同じようにコンパイルされますが、f # スタイルは f # の呼び出し元が f # スタイルのパラメーターアプリケーションとを使用するように強制します。NET スタイルでは、F # の呼び出し元がタプル引数アプリケーションを使用するように強制されます。

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a>クラス型を使用したインターフェイスの実装

`interface`次のコードに示すように、キーワード、インターフェイスの名前、およびキーワードを使用して、クラス型に1つ以上のインターフェイスを実装することができ `with` ます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

インターフェイスの実装は継承されるため、派生クラスはそれらを再実装する必要はありません。

## <a name="calling-interface-methods"></a>インターフェイスメソッドの呼び出し

インターフェイスメソッドを呼び出すことができるのは、インターフェイスを実装する型のオブジェクトではなく、インターフェイスのみです。 そのため、これらのメソッドを呼び出すには、演算子または演算子を使用して、インターフェイス型にアップキャストすることが必要になる場合があり `:>` `upcast` ます。

型のオブジェクトがある場合にインターフェイスメソッドを呼び出すには、 `SomeClass` 次のコードに示すように、オブジェクトをインターフェイス型にアップキャストする必要があります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

別の方法として、次の例のように、キャストしてインターフェイスメソッドを呼び出すオブジェクトに対してメソッドを宣言する方法があります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>オブジェクト式を使用したインターフェイスの実装

オブジェクト式は、インターフェイスを実装するための簡単な方法を提供します。 これらは、名前付きの型を作成する必要がなく、インターフェイスメソッドをサポートするオブジェクトを必要とする場合に、追加のメソッドを使用しない場合に便利です。 オブジェクト式を次のコードに示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>インターフェイスの継承

インターフェイスは、1つまたは複数の基本インターフェイスから継承できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="implementing-interfaces-with-default-implementations"></a>既定の実装でのインターフェイスの実装

C# では、次のように、既定の実装でインターフェイスを定義できます。

```csharp
using System;

namespace CSharp
{
    public interface MyDim
    {
        public int Z => 0;
    }
}
```

これらは F # から直接利用できます。

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

仮想メンバーをオーバーライドするのと同様に、を使用して既定の実装をオーバーライドでき `override` ます。

既定のを実装していないインターフェイスのメンバーは、引き続き明示的に実装する必要があります。

## <a name="implementing-the-same-interface-at-different-generic-instantiations"></a>異なるジェネリックインスタンスでの同じインターフェイスの実装

F # では、次のように、異なるジェネリックインスタンスで同じインターフェイスを実装できます。

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

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [オブジェクト式](object-expressions.md)
- [クラス](classes.md)
