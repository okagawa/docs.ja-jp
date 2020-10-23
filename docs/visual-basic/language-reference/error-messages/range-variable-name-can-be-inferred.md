---
title: 範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: 63990b7d37388057ff2cdb430d29878a1c7b39ba
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162363"
---
# <a name="bc36599-range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>BC36599:範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます

1 つ以上の引数を取るプログラミング要素が、LINQ クエリに含まれています。 コンパイラは、そのプログラミング要素から範囲変数を推論できません。

**エラー ID:** BC36599

## <a name="to-correct-this-error"></a>このエラーを解決するには

次のコードに示すように、プログラミング要素に明示的な変数名を指定します。

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Select 句](../queries/select-clause.md)
