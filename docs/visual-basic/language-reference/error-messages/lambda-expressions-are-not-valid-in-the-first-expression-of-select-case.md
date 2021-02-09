---
description: "詳細情報: BC36635:ラムダ式は、'Select Case' ステートメントの最初の式では有効ではありません"
title: ラムダ式は、'Select Case' ステートメントの最初の式では有効ではありません
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: e0c388db7164f6c9f99ba917109593a796f7b23b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795938"
---
# <a name="bc36635-lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a>BC36635:ラムダ式は、'Select Case' ステートメントの最初の式では有効ではありません

ラムダ式は、`Select Case` ステートメントのテスト式に使用できません。 ラムダ式の定義では関数を返しますが、`Select Case` ステートメントのテスト式は基本データ型である必要があります。

 次のコードではこのエラーが発生します。

```vb
' Select Case (Function(arg) arg Is Nothing)
    ' List of the cases.
' End Select
```

 **エラー ID:** BC36635

## <a name="to-correct-this-error"></a>このエラーを解決するには

- コードを調べて、 `If...Then...Else` ステートメントなどの別の条件構造を使用できないかをご確認ください。

- 次のコードに示すように、関数を呼び出そうとした可能性があります。

```vb
Dim num? As Integer
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))
    ' List of the cases
End Select
```

## <a name="see-also"></a>関連項目

- [ラムダ式](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [If...Then...Else ステートメント](../statements/if-then-else-statement.md)
- [Select...Case ステートメント](../statements/select-case-statement.md)
