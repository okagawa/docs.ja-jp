---
title: スライス
description: '既存の F # データ型にスライスを使用する方法、およびその他のデータ型用に独自のスライスを定義する方法について説明します。'
ms.date: 12/23/2019
ms.openlocfilehash: a3920ad9e1b205b506aaee92c4606bcebf94feba
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557078"
---
# <a name="slices"></a>スライス

F # では、スライスは、その `GetSlice` 定義またはスコープ内の [型拡張](type-extensions.md)でメソッドを持つ任意のデータ型のサブセットです。 これは、F # の配列とリストで最もよく使用されます。 この記事では、既存の F # 型からスライスを取得する方法と、独自のスライスを定義する方法について説明します。

スライスは [インデクサー](./members/indexed-properties.md)に似ていますが、基になるデータ構造から1つの値を生成するのではなく、複数の値を生成します。

現在、F # には、文字列、リスト、配列、および2D 配列をスライスするための組み込みサポートがあります。

## <a name="basic-slicing-with-f-lists-and-arrays"></a>F # リストと配列を使用した基本的なスライス

スライスされる最も一般的なデータ型は、F # のリストと配列です。 次の例では、リストを使用してこれを行う方法を示します。

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

配列のスライスは、スライスリストと同じです。

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a>多次元配列のスライス

F # は、F # コアライブラリの多次元配列をサポートしています。 1次元配列の場合と同様に、多次元配列のスライスも役に立ちます。 ただし、追加のディメンションの導入では、特定の行と列のスライスを取得できるように、若干異なる構文が必要になります。

次の例は、2D 配列をスライスする方法を示しています。

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

現在、F # コアライブラリでは、 `GetSlice` 3d 配列に対して定義されていません。 3D 配列やその他の次元の配列をスライスする場合は、自分でメンバーを定義 `GetSlice` します。

## <a name="defining-slices-for-other-data-structures"></a>他のデータ構造のスライスの定義

F # コアライブラリでは、型の限られたセットのスライスが定義されています。 より多くのデータ型に対してスライスを定義する場合は、型定義自体または型拡張機能のいずれかを使用できます。

たとえば、クラスのスライスを定義して、 <xref:System.ArraySegment%601> 便利なデータ操作を可能にする方法を次に示します。

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

型と型を使用するもう1つの例を <xref:System.Span%601> <xref:System.ReadOnlySpan%601> 次に示します。

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a>組み込みの F # スライスは両端を含みます

F # のすべての組み込みスライスは、終了します。つまり、上限がスライスに含まれます。 開始インデックスと終了インデックスを持つ特定のスライスの場合、結果として得られるスライスには `x` `y` *yth* 値が含まれます。

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a>組み込みの F # 空のスライス

F # のリスト、配列、シーケンス、文字列、2D 配列、3D 配列、および4D 配列では、存在しないスライスが生成される場合、空のスライスが生成されます。

以下、具体例に沿って説明します。

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

C# 開発者は、空のスライスを生成するのではなく、例外をスローすることを期待できます。 これは、空のコレクションが F # で構成されるという事実をルートとする設計上の決定です。 空の F # リストは、別の F # リストで構成できます。また、空の文字列を既存の文字列に追加することもできます。 パラメーターとして渡された値に基づいてスライスを取り、空のコレクションを生成することによって、F # コードの合成特性に適合するようにすることは、一般的な場合があります。

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a>3D および4D 配列の固定インデックススライス

F # 3D および4D 配列の場合は、特定のインデックスを "修正" し、そのインデックスが固定されている他のディメンションをスライスできます。

これを説明するために、次の3D 配列について考えてみます。

*z = 0*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 0 | 1 |
| **1** | 2 | 3 |

*z = 1*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 4 | 5 |
| **1** | 6 | 7 |

配列からスライスを抽出する場合は `[| 4; 5 |]` 、固定インデックススライスを使用します。

```fsharp
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

最後の行は、 `y` `z` 3d 配列のと決まっを修正し、 `x` マトリックスに対応する残りの値を取得します。

## <a name="see-also"></a>関連項目

- [インデックス付きプロパティ](./members/indexed-properties.md)
