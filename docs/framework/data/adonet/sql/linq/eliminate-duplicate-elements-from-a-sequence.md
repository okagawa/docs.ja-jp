---
description: '詳細情報: シーケンスからの重複する要素の削除'
title: シーケンスからの重複する要素の削除
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: f371fc27794361e3ea92d342f845996d9291d30c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786096"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>シーケンスからの重複する要素の削除

重複する要素をシーケンスから削除するには、<xref:System.Linq.Queryable.Distinct%2A> 演算子を使用します。  
  
## <a name="example"></a>例  

 次の例では、<xref:System.Linq.Queryable.Distinct%2A> を使用して、顧客の住所がある市のシーケンスを選択します。それぞれの市はシーケンス内で重複しません。  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>関連項目

- [クエリの例](query-examples.md)
