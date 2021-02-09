---
description: '詳細情報: IsNot 演算子 (Visual Basic)'
title: IsNot 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ac3e127676dfa57d14e07838152022de62fc336b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665667"
---
# <a name="isnot-operator-visual-basic"></a>IsNot 演算子 (Visual Basic)

2 つのオブジェクト参照変数を比較します。

## <a name="syntax"></a>構文

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>指定項目

- `result`

  必須です。 `Boolean` 値。

- `object1`

  必須です。 任意の `Object` 変数または式。

- `object2`

  必須。 任意の `Object` 変数または式。

## <a name="remarks"></a>Remarks

`IsNot` 演算子は、2 つのオブジェクト参照が別のオブジェクトを参照しているかどうかを判断します。 ただし、値は比較されません。 `object1` と `object2` の両方がまったく同じオブジェクト インスタンスを参照している場合、`result` は `False` です。そうでない場合、`result` は `True` です。

`IsNot` は `Is` 演算子の逆です。 `IsNot` の利点は、`Not` と `Is` を使用することで読みにくくなる可能性がある洗練されていない構文を回避できることです。

 `Is` と `IsNot` の演算子を使用すると、事前バインディング オブジェクトと遅延バインディング オブジェクトの両方をテストできます。

## <a name="example"></a>例

次のコード例では、`Is` 演算子と `IsNot` 演算子の両方を使用して、同じ比較を実行します。

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a>TypeOf 演算子と IsNot 演算子を使用する

Visual Basic 14 以降、`TypeOf` 演算子と `IsNot` 演算子を一緒に使用し、オブジェクトとデータ型の間に互換性が "*ない*" かどうかをテストできます。 次に例を示します。

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a>関連項目

- [Is 演算子](is-operator.md)
- [TypeOf 演算子](typeof-operator.md)
- [Visual Basic における演算子の優先順位](operator-precedence.md)
- [方法: 2 つのオブジェクトが等しいかどうかをテストする](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
