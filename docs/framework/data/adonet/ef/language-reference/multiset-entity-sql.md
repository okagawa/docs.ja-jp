---
description: '詳細情報: MULTISET (Entity SQL)'
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: f963638d018299e1cae7435f6dd3b7eaf855b4eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696595"
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)

値のリストからマルチセットのインスタンスを作成します。 MULTISET コンストラクターの値はすべて、互換性のある型 `T`である必要があります。 空のマルチセット コンストラクターは使用できません。

## <a name="syntax"></a>構文

```sql
MULTISET ( expression [{, expression }] )
-- or
{ expression [{, expression }] }
```

## <a name="arguments"></a>引数

`expression`  
 任意の有効な値のリスト。

## <a name="return-value"></a>戻り値

型 MULTISET\<T> のコレクション。

## <a name="remarks"></a>Remarks

<!-- markdownlint-disable DOCSMD001 -->

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] には、行コンストラクター、オブジェクト コンストラクター、およびマルチセット (またはコレクション) コンストラクターの 3 種類のコンストラクターが用意されています。 詳しくは、「[コンストラクター](constructing-types-entity-sql.md)」をご覧ください。

マルチセット コンストラクターは、値のリストからマルチセットのインスタンスを作成します。 このコンストラクターの値はすべて、互換性のある型である必要があります。

たとえば、次の式は整数のマルチセットを作成します。

`MULTISET(1, 2, 3)`

`{1, 2, 3}`

> [!NOTE]
> 入れ子になったマルチセット リテラルは、`{{1, 2, 3}}` のように、外側のマルチセットに含まれているマルチセット要素が 1 つである場合にのみサポートされます。 複数のマルチセット要素が外側のマルチセットに含まれている場合 ( `{{1, 2}, {3, 4}}`など)、入れ子になったマルチセット リテラルはサポートされません。

## <a name="example"></a>例

次の Entity SQL クエリでは、MULTISET 演算子を使用して、値のリストからマルチセットのインスタンスを作成します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。

1. 「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。

2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。

[!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]

## <a name="see-also"></a>関連項目

- [コンストラクター](constructing-types-entity-sql.md)
- [Entity SQL リファレンス](entity-sql-reference.md)
