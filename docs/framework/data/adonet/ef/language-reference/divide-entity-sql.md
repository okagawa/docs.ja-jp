---
description: '詳細情報: / (除算) (Entity SQL)'
title: '- (除算) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 4ac487c636c460401eeb147dc7ce1a8d8ba7f7ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724636"
---
# <a name="-divide-entity-sql"></a>/ (除算) (Entity SQL)

1 つの値を別の値で除算します。  
  
## <a name="syntax"></a>構文  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a>引数  

 `dividend`  
 除算する数値式。 `dividend` は、任意の数値データ型の有効な式です。  
  
 `divisor`  
 被除数を除算する数値式。 `divisor` は、任意の数値データ型の有効な式です。  
  
## <a name="result-types"></a>戻り値の型  

 2 つの引数の暗黙の型の昇格の結果であるデータ型。 暗黙の型の昇格について詳しくは、「[型システム](type-system-entity-sql.md)」をご覧ください。  
  
## <a name="example"></a>例  

 次の Entity SQL クエリでは、/ 算術演算子を使用して 2 つの数値の間で除算をします。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
