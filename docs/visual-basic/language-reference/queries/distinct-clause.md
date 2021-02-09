---
description: '詳細情報: Distinct 句 (Visual Basic)'
title: Distinct 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: df1cdc58f7af406533e67a396a958a26b0c79635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700651"
---
# <a name="distinct-clause-visual-basic"></a>Distinct 句 (Visual Basic)

現在の範囲変数の値を制限して、後続のクエリ結果内で重複する値を除去します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>Remarks  

 `Distinct` 句を使用して、一意の項目の一覧を返すことができます。 `Distinct` 句によって、クエリで重複するクエリ結果を無視させます。 `Distinct` 句は、`Select` 句で指定されたすべての戻りフィールドの重複する値に適用されます。 `Select` 句が指定されていない場合、`Distinct` 句は `From` 句で識別されたクエリの範囲変数に適用されます。 範囲変数が変更できない型である場合、クエリでは、その型のすべてのメンバーが既存のクエリの結果と一致する場合にのみ、クエリの結果が無視されます。  
  
## <a name="example"></a>例  

 次のクエリ式では、顧客の一覧と顧客の注文の一覧が結合されます。 一意の顧客名と注文日の一覧を返すために、`Distinct` 句が含まれています。  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](index.md)
- [From 句](from-clause.md)
- [Select 句](select-clause.md)
- [WHERE 句](where-clause.md)
