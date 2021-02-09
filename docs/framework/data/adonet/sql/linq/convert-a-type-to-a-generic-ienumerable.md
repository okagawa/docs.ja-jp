---
description: '詳細情報: 汎用 IEnumerable への型の変換'
title: 汎用 IEnumerable への型の変換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: 9be9022bce84808e18514937116ea962065dc1a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712520"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>汎用 IEnumerable への型の変換

汎用 <xref:System.Linq.Enumerable.AsEnumerable%2A> として型指定された引数を返すには、`IEnumerable` を使用します。  
  
## <a name="example"></a>例  

 この例では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (既定の汎用 `Query` を使用) は、クエリを SQL に変換し、サーバー上での実行を試みます。 しかし、`where` 句が、SQL に変換できない、ユーザー定義のクライアント側メソッド (`isValidProduct`) を参照しています。  
  
 これを解決するには、クライアント側の汎用 <xref:System.Collections.Generic.IEnumerable%601> 実装の `where` を指定し、汎用 <xref:System.Linq.IQueryable%601> を置き換えます。 <xref:System.Linq.Enumerable.AsEnumerable%2A> 演算子を呼び出すことによって、これを行います。  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>関連項目

- [クエリの例](query-examples.md)
