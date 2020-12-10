---
title: null 許容値型
description: 'F # で null にすることもできる値の型を表す方法である null 許容値型の使用方法について説明します。'
ms.date: 11/19/2020
ms.openlocfilehash: e28cbfc57c5631573f46ac36462517cf011e96d2
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009639"
---
# <a name="nullable-value-types"></a>null 許容値型

_Null 許容値型_ は、 `Nullable<'T>` になる可能性がある任意の [構造体](structures.md)型を表し `null` ます。 これは、これらの種類の型 (整数など) を表すことができるようなライブラリやコンポーネントと対話する場合に便利です `null` 。 このコンストラクトをバッキングする基になる型は <xref:System.Nullable%601?displayProperty=nameWithType> です。

## <a name="syntax"></a>構文

```fsharp
Nullable<'T>
Nullable value
```

## <a name="declare-and-assign-with-values"></a>値を指定して宣言して代入

Null 許容値型の宣言は、F # でのラッパーのような型の宣言と同じです。

```fsharp
open System

let x = 12
let nullableX = Nullable<int> x
```

ジェネリック型パラメーターを除外して、型の推定によって解決できるようにすることもできます。

```fsharp
open System

let x = 12
let nullableX = Nullable x
```

Null 許容値型に割り当てるには、明示的にする必要もあります。 F # で定義された null 許容値型には暗黙的な変換はありません。

```fsharp
open System

let mutable x = Nullable 12
x <- Nullable 13
```

## <a name="assign-null"></a>Null を割り当てる

Null 許容値型に直接割り当てることはできません `null` 。 代わりにを使用し `Nullable()` ます。

```fsharp
let mutable a = Nullable 42
a <- Nullable()
```

これは、に `Nullable<'T>` `null` 適切な値が設定されていないためです。

## <a name="pass-and-assign-to-members"></a>メンバーへの引き渡しと割り当て

メンバーを操作する場合と F # 値を使用する場合の主な違いは、メンバーを操作するときに null 許容値型を暗黙的に推論できることです。 Null 許容値型を入力として受け取る次のメソッドについて考えてみます。

```fsharp
type C() =
    member _.M(x: Nullable<int>) = x.HasValue
    member val NVT = Nullable 12 with get, set

let c = C()
c.M(12)
c.NVT <- 12
```

前の例では、メソッドにを渡すことができ `12` `M` ます。 自動プロパティに割り当てることもでき `12` `NVT` ます。 入力を null 許容値型として構築し、それがターゲット型と一致する場合、F # コンパイラはこのような呼び出しや割り当てを暗黙的に変換します。

## <a name="examine-a-nullable-value-type-instance"></a>Null 許容値型インスタンスを調べる

使用可能な値を表す一般化されたコンストラクトである [オプション](options.md)とは異なり、null 許容値型はパターンマッチングでは使用されません。 代わりに、式を使用してプロパティを確認する必要があり [`if`](conditional-expressions-if-then-else.md) `HasValue` ます。

基になる値を取得するには、次のよう `Value` に、チェックの後にプロパティを使用し `HasValue` ます。

```fsharp
open System

let a = Nullable 42

if a.HasValue then
    printfn $"{a} is {a.Value}"
else
    printfn $"{a} has no value."
```

## <a name="nullable-operators"></a>Null 許容の演算子

算術または比較など、null 許容値型に対する操作では、 [null 許容演算子](symbol-and-operator-reference/nullable-operators.md)を使用する必要があります。

名前空間の変換演算子を使用して、null 許容値型から別の型に変換でき `FSharp.Linq` ます。

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt
```

また、適切な null 非許容演算子を使用してプリミティブ型に変換し、値がない場合は例外が発生しないようにすることもできます。

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

printfn $"value is %f{float nullableFloat}"
```

また、次のように、null 値を許容する演算子を使用することもでき `HasValue` `Value` ます。

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

let isBigger = nullableFloat ?> 1.0
let isBiggerLongForm = nullableFloat.HasValue && nullableFloat.Value > 1.0
```

比較では、 `?>` 左辺が null 値が許容されるかどうかを確認し、値がある場合にのみ成功します。 これは、その後の行に相当します。

## <a name="see-also"></a>関連項目

- [構造体](structures.md)
- [F # オプション](options.md)
