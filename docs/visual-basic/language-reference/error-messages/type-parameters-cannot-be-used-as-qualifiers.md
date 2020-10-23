---
title: 型パラメーターは修飾子として使用できません。
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 14e6094b0cc129eba86db1808c0f0575955f5e75
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161193"
---
# <a name="bc32098-type-parameters-cannot-be-used-as-qualifiers"></a>BC32098:型パラメーターは修飾子として使用できません。

プログラミング要素は、型パラメーターを含む修飾文字列で修飾されます。

型パラメーターは、ジェネリック型が構築されるときに指定される型の要件を表します。 これは定義されている特定の型を表していません。 修飾文字列には、コンパイル時に定義された要素のみを含める必要があります。

次のコードでは、このエラーが生成される可能性があります。

```vb
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean

    Dim saveText As c.Text
    ' Insert code to look for badText within saveText.
End Function
```

 **エラー ID:** BC32098

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 修飾文字列から型パラメーターを削除するか、それを定義済みの型で置き換えます。

2. 構築された型を使用して、修飾するプログラミング要素を見つける必要がある場合は、追加のプログラム ロジックを使用する必要があります。

## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [型リスト](../statements/type-list.md)
