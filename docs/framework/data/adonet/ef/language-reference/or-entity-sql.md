---
description: '詳細情報: || (OR) (Entity SQL)'
title: '|| (OR) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 83af0211de1dd86b057237c36312e3ce33a3512a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696335"
---
# <a name="-or-entity-sql"></a>|| (OR) (Entity SQL)

2 つの `Boolean` 式を結合します。  
  
## <a name="syntax"></a>構文  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>引数  

 `boolean_expression`  
 `Boolean`値を返す任意の有効な式。  
  
## <a name="return-value"></a>戻り値  

 いずれかの条件が`true` の場合は `true`、それ以外の場合は `false`。  
  
## <a name="remarks"></a>Remarks  

 OR は [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の論理演算子です。 2 つの条件を結合する場合に使用します。 1 つのステートメント内に複数の論理演算子が使われている場合、OR 演算子は AND 演算子の次に評価されます。 ただし、かっこを使うと、演算の順序を変更することができます。  
  
 二重の縦棒 (&#124;&#124;) は、OR 演算子と同じ効果を持ちます。  
  
 使用可能な入力値と戻り値の型を次の表に示します。  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|true|true|true|  
|`FALSE`|true|false|NULL|  
|`NULL`|true|NULL|NULL|  
  
## <a name="example"></a>例  

 次の Entity SQL クエリでは、OR 演算子を使用して 2 つの `Boolean` 式を結合します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
