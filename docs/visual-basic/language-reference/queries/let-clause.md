---
title: Let 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 4bf832651d9753c41ee5a02defec4adc55af1ff1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359762"
---
# <a name="let-clause-visual-basic"></a>Let 句 (Visual Basic)
値を計算し、その値をクエリ内の新しい変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`variable`|必須です。 指定された式の結果を参照するために使用できる別名。|  
|`expression`|必須です。 評価され、指定された変数に割り当てられる式。|  
  
## <a name="remarks"></a>Remarks  
 `Let` 句を使用すると、各クエリ結果の値を計算し、別名を使用してその値を参照できます。 別名は、`Where` 句などの他の句で使用できます。 `Let` 句を使用すると、クエリに含まれる式の句の別名を指定し、その式の句が使用されるたびに別名を置き換えることができるため、読みやすいクエリ ステートメントを作成できます。  
  
 `Let` 句には、任意の数の `variable` と `expression` の代入を含めることができます。 各代入はコンマ (,) で区切ります。  
  
## <a name="example"></a>例  
 次のコード例では、`Let` 句を使用して、製品に対して 10% の割引を計算します。  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](index.md)
- [Select 句](select-clause.md)
- [From 句](from-clause.md)
- [WHERE 句](where-clause.md)
