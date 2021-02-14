---
description: '詳細情報: + (加算)'
title: + (追加)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b8ec9f50b349fe971513f399b7e9984e9044cf58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697310"
---
# <a name="-add"></a>+ (加算)

2 つの値を加算します。  
  
## <a name="syntax"></a>構文  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a>引数  

 `expression`  
 任意の数値データ型の有効な式。  
  
## <a name="result-types"></a>戻り値の型  

 2 つの引数の暗黙の型の昇格の結果であるデータ型。 暗黙の型の昇格について詳しくは、「[型システム](type-system-entity-sql.md)」をご覧ください。  
  
## <a name="remarks"></a>Remarks  

 EDM.String 型の場合は、値が連結されます。  
  
## <a name="example"></a>例  

 次の Entity SQL クエリでは、+ 算術演算子を使用して 2 つの数値を加算します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
- [概念モデルの型 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
