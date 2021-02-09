---
description: '詳細情報: 2 つのシーケンスの和集合の取得'
title: 2 つのシーケンスの和集合の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 5541316560c05712e22c54f706b02d868fadb381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662963"
---
# <a name="return-the-set-union-of-two-sequences"></a>2 つのシーケンスの和集合の取得

2 つのシーケンスの和集合を返すには、<xref:System.Linq.Queryable.Union%2A> 演算子を使用します。  
  
## <a name="example"></a>例  

 この例では、<xref:System.Linq.Queryable.Union%2A> を使用して、`Customers` と `Employees` のいずれかが居住しているすべての国と地域のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Linq.Queryable.Union%2A> 演算子は、マルチセットの順序なし連結演算子として、マルチセットに対して定義されます (事実上、SQL の [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) 句の結果)。

詳細な情報と例については、「<xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>」を参照してください。
  
## <a name="see-also"></a>関連項目

- [クエリの例](query-examples.md)
- [標準クエリ演算子の変換](standard-query-operator-translation.md)
