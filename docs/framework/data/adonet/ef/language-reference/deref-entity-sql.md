---
description: '詳細情報: DEREF (Entity SQL)'
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 9d0f29123c1459c6eab21ea9cd860b5c9e77f591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724727"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)

参照値を逆参照し、その逆参照の結果を生成します。  
  
## <a name="syntax"></a>構文  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a>引数  

 `expression`  
 コレクションを返す任意の有効なクエリ式。  
  
## <a name="return-value"></a>戻り値  

 参照されるエンティティの値。  
  
## <a name="remarks"></a>Remarks  

 DEREF 演算子は参照値を逆参照し、その逆参照の結果を生成します。 たとえば、`r` が ref\<T> 型の参照である場合、`Deref(r)` は `r` によって参照されるエンティティを生成する `T` 型の式です。 参照値が null または未解決 (つまり、参照先が存在しない) の場合、DEREF 演算子の結果は null になります。  
  
## <a name="example"></a>例  

 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、DEREF 演算子を使用して参照値を逆参照し、その逆参照の結果を生成します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として ExecutePrimitiveTypeQuery メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
- [REF](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [NULL 値が許容される構造化型](nullable-structured-types-entity-sql.md)
