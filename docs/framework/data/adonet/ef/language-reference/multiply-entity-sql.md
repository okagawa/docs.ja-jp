---
description: '詳細情報: * (乗算) (Entity SQL)'
title: '* (乗算) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 92606e5f9e4646ab651d0e07095e6f419401188f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696621"
---
# <a name="-multiply-entity-sql"></a>* (乗算) (Entity SQL)

2 つの式を乗算します。  
  
## <a name="syntax"></a>構文  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a>引数  

 `expression`  
 任意の数値データ型の有効な式。  
  
## <a name="result-types"></a>戻り値の型  

 2 つの引数の暗黙の型の昇格の結果であるデータ型。 暗黙の型の昇格について詳しくは、「[型システム](type-system-entity-sql.md)」をご覧ください。  
  
## <a name="example"></a>例  

 次の Entity SQL クエリでは、* 算術演算子を使用して 2 つの数値を乗算します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
