---
description: '詳細情報: クエリ式 (Entity SQL)'
title: クエリ式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 218e7db0e812bd43a92d3145bc4bf96244ef6a3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696036"
---
# <a name="query-expressions-entity-sql"></a>クエリ式 (Entity SQL)

クエリ式とは、さまざまなクエリ演算子を組み合わせて 1 つの構文にしたものです。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] には、[リテラル](literals-entity-sql.md)、[パラメーター](parameters-entity-sql.md)、[変数](variables-entity-sql.md)、演算子、[関数](functions-entity-sql.md)、集合演算子などのさまざまな種類の式が用意されています。 詳細については、「[Entity SQL リファレンス](entity-sql-reference.md)」をご覧ください。  
  
## <a name="clauses"></a>句  

 クエリ式は、オブジェクトのコレクションに連続した操作を適用する一連の句で構成されます。 これらは、標準の SQL select ステートメントと同じ句に基づいています:[SELECT](select-entity-sql.md)、[FROM](from-entity-sql.md)、[WHERE](where-entity-sql.md)、[GROUP BY](group-by-entity-sql.md)、[HAVING](having-entity-sql.md)、および [ORDER BY](order-by-entity-sql.md)。  
  
## <a name="scope"></a>スコープ  

 FROM 句で定義された名前は、出現順 (左から右の順) に FROM スコープに導入されます。 JOIN リストでは、式は既にリストで定義されている名前を参照できます。 FROM 句で指定された要素のパブリック プロパティは FROM スコープに追加されません。それらは常に、別名で修飾された名前を使用して参照する必要があります。 通常は、SELECT 式のすべての部分が FROM スコープに含まれると見なされます。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
