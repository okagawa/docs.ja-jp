---
description: '詳細情報: THEN (Entity SQL)'
title: THEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: e1f0657cfef3786832f489434fd8fc0342e8687b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673467"
---
# <a name="then-entity-sql"></a>THEN (Entity SQL)

WHEN 句が `true`として評価された場合の結果です。  
  
## <a name="syntax"></a>構文  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>引数  

 `when_expression`  
 任意の有効なブール式。  
  
 `then_expression`  
 コレクションを返す任意の有効なクエリ式。  
  
## <a name="remarks"></a>Remarks  

 `when_expression` が `true`として評価された場合、対応する `then-expression`が評価されます。 WHEN の条件が満たされなかった場合は、 `else-expression` が評価されます。 ただし、 `else-expression`が存在しない場合、結果は NULL になります。  
  
 例については、「[CASE](case-entity-sql.md)」を参照してください。  
  
## <a name="example"></a>例  

 次の Entity SQL クエリでは、CASE 式を使用して、一連の `Boolean` 式を評価します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a>関連項目

- [CASE](case-entity-sql.md)
- [Entity SQL リファレンス](entity-sql-reference.md)
