---
description: '詳細情報: BC36629:Null 許容型の推論はこのコンテキストではサポートされていません'
title: Null 許容型の推論はこのコンテキストではサポートされていません
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 915f964d55068f39b0468e2c47cc6e5538be1a6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795626"
---
# <a name="bc36629-nullable-type-inference-is-not-supported-in-this-context"></a>BC36629:Null 許容型の推論はこのコンテキストではサポートされていません

値の型と構造体は、Null 許容と宣言できます。

```vb
Dim a? As Integer
Dim b As Integer?
```

 ただし、Null 許容の宣言を型の推定と組み合わせて使用することはできません。 次の例では、このエラーが発生します。

```vb
' Not valid.
' Dim c? = 10
' Dim d? = a
```

 **エラー ID:** BC36629

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `As` 句を使用して、変数を null 許容値型として宣言します。

## <a name="see-also"></a>関連項目

- [null 許容値型](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [ローカル型の推論](../../programming-guide/language-features/variables/local-type-inference.md)
