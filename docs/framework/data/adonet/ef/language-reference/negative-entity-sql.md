---
description: '詳細情報: - (負符号) (Entity SQL)'
title: '- (負符号) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: f3d30ce36b95e44755d148dc06279f67f15b0664
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712884"
---
# <a name="--negative-entity-sql"></a>- (負符号) (Entity SQL)

数値式の負の値を返します。  
  
## <a name="syntax"></a>構文  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a>引数  

 `expression`  
 任意の数値データ型の有効な式。  
  
## <a name="result-types"></a>戻り値の型  

 `expression`のデータ型。  
  
## <a name="remarks"></a>Remarks  

 符号なしの型を `expression` に指定した場合、戻り値の型は、 `expression`の型と最も関連性の高い符号付きの型になります。 たとえば、 `expression` に Byte 型を指定した場合、Int16 型の値が返されます。  
  
## <a name="example"></a>例  

 次の Entity SQL クエリでは、- 算術演算子を使用して、数値式の負の値を返します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
