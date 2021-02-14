---
description: '詳細情報: ! (NOT) (Entity SQL)'
title: '! (NOT) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 648cc4ff73769ae280570b2d42934b2001fa5182
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696452"
---
# <a name="-not-entity-sql"></a>! (NOT) (Entity SQL)

`Boolean` 型の式を否定します。  
  
## <a name="syntax"></a>構文  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a>引数  

 `boolean_expression`  
 ブール値を返す任意の有効な式。  
  
## <a name="remarks"></a>Remarks  

 感嘆符 (!) には、NOT 演算子と同じ機能があります。  
  
## <a name="example"></a>例  

 次の Entity SQL クエリでは、NOT 演算子を使用して `Boolean` 型の式を否定します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
