---
description: '詳細情報: IN (Entity SQL)'
title: IN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 234ed15430e44d12d4ca7c98fcb4a7bc03d117f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748597"
---
# <a name="in-entity-sql"></a>IN (Entity SQL)

コレクション内に一致する値があるかどうかを調べます。  
  
## <a name="syntax"></a>構文  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>引数  

 `value`  
 照合する値を返す任意の有効な式。  
  
 [ NOT ]  
 IN の `Boolean` 型の結果を否定することを指定します。  
  
 `expression`  
 一致の判定対象のコレクションを返す任意の有効な式。 すべての式は、 `value`と同じ型であるか、共通の基本型または派生型である必要があります。  
  
## <a name="return-value"></a>戻り値  

 コレクションに値が見つかった場合は `true`、値が null またはコレクションが null の場合は null、それ以外の場合は `false` が返されます。 NOT IN を使用すると、IN の結果が否定されます。  
  
## <a name="example"></a>例  

 次の Entity SQL クエリでは、IN 演算子を使用して、コレクション内に一致する値があるかどうかを調べます。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
