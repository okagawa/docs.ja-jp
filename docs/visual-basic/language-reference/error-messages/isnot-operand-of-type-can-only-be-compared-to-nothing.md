---
description: "詳細情報: BC32128:'typename' は Null 許容型であるため、'typename' 型の 'IsNot' オペランドは 'Nothing' とのみ比較できます"
title: "'typename' は Null 許容型であるため、'typename' 型の 'IsNot' オペランドは 'Nothing' とのみ比較できます"
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 732c8bee2ae352824c7d50bba8b2b35598d6f53b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795990"
---
# <a name="bc32128-isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>BC32128:'typename' は Null 許容型であるため、'typename' 型の 'IsNot' オペランドは 'Nothing' とのみ比較できます

Null 許容値型として宣言された変数が、`Nothing` 演算子を使用して、`IsNot` 以外の式と比較されました。

**エラー ID:** BC32128

## <a name="to-correct-this-error"></a>このエラーを解決するには

`Nothing` 演算子を使用して、Null 許容型を `IsNot` 以外の式と比較するには、次の例に示すように、Null 許容型に対して `GetType` メソッドを呼び出し、その結果を式と比較します。

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a>関連項目

- [null 許容値型](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [IsNot 演算子](../operators/isnot-operator.md)
