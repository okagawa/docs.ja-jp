---
title: 配列 - C# プログラミング ガイド
description: C# の配列データ構造に、同じ型の複数の変数を格納します。 配列を宣言するには、型を指定するか、任意の型を格納する場合は Object を指定します。
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 203d8b86da4e74d8c5397132a0ba68618eedf348
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794765"
---
# <a name="arrays-c-programming-guide"></a>配列 (C# プログラミング ガイド)

配列データ構造体には、同じ型の複数の変数を格納できます。 配列は、要素の型を指定することで宣言します。 配列に任意の型の要素を格納する場合は、その型として `object` を指定できます。 C# の統一型システムでは、すべての型 (定義済み、ユーザー定義、参照型、および値の型) が、直接または間接的に <xref:System.Object> を継承します。

```csharp
type[] arrayName;
```

## <a name="example"></a>例

次の例では、1 次元配列、多次元配列、およびジャグ配列を作成しています。

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>配列の概要

配列には、次の特徴があります。

- 配列は、[1 次元](single-dimensional-arrays.md)、[多次元](multidimensional-arrays.md)、または[ジャグ](jagged-arrays.md)のいずれかになります。
- 次元数と各次元の長さは、配列インスタンスの作成時に設定されます。 インスタンスの有効期間中にこれらの値を変更することはできません。
- 数値配列要素の既定値はゼロに設定され、参照要素は null に設定されます。
- ジャグ配列は配列の配列です。そのため、配列要素は参照型で、`null` に初期化されます。
- 配列には、ゼロから始まるインデックスが付けられます。`n` 個の要素を含む配列には、`0` から `n-1` までのインデックスが付けられます。
- 配列の要素および配列型は、どのような型でもかまいません。
- 配列型は、抽象基本型 <xref:System.Array> から派生した[参照型](../../language-reference/keywords/reference-types.md)です。 この型は <xref:System.Collections.IEnumerable> と <xref:System.Collections.Generic.IEnumerable%601> を実装するので、C# のすべての配列で [foreach](../../language-reference/keywords/foreach-in.md) 反復処理を使用できます。

### <a name="arrays-as-objects"></a>オブジェクトとしての配列

C# の配列は、実際はオブジェクトです。C や C++ の場合のように、単なるアドレス指定可能な連続メモリ領域ではありません。 <xref:System.Array> はすべての配列型の抽象基本データ型で、 <xref:System.Array> のプロパティとその他のクラス メンバーを使用できます。 この例としては、<xref:System.Array.Length%2A> プロパティを使用して、配列の長さを取得します。 `numbers` 配列の長さ `5` を `lengthOfNumbers` という変数に代入するコードは、次のようになります。

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<xref:System.Array> クラスには、配列の並べ替え、検索、コピーを行うための便利なメソッドやプロパティが他にも多数用意されています。 次の例では、<xref:System.Array.Rank%2A> プロパティを使用して、配列の次元数を表示します。

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>関連項目

- [1 次元配列の使用方法](single-dimensional-arrays.md)
- [多次元配列の使用方法](multidimensional-arrays.md)
- [ジャグ配列の使用方法](jagged-arrays.md)
- [配列での foreach の使用](using-foreach-with-arrays.md)
- [引数としての配列の受け渡し](passing-arrays-as-arguments.md)
- [暗黙的に型指定される配列](implicitly-typed-arrays.md)
- [C# プログラミング ガイド](../index.md)
- [コレクション](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
