---
description: '詳細情報: ID キャッシュからのオブジェクトの取得'
title: ID キャッシュからのオブジェクトの取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 1f3d5f839a6fff33d62d4e0cb2281bd087f2d320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695087"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>ID キャッシュからのオブジェクトの取得

このトピックでは、<xref:System.Data.Linq.DataContext> によって管理される ID キャッシュからオブジェクトを返す、LINQ to SQL クエリの種類について説明します。  
  
 LINQ to SQL では、<xref:System.Data.Linq.DataContext> がクエリの実行に応じてオブジェクトの ID を ID キャッシュにログして、オブジェクトを管理する場合があります。 場合によっては、データベースに対してクエリを実行する前に、LINQ to SQL が ID キャッシュからオブジェクトの取得を試みることがあります。  
  
 通常、LINQ to SQL で ID キャッシュからオブジェクトを取得するには、そのクエリがオブジェクトのプライマリ キーに基づき、1 つのオブジェクトを返すようにする必要があります。 特に、次に示す一般的な形式のいずれかでクエリを実行する必要があります。  
  
> [!NOTE]
> プリコンパイル済みクエリでは、ID キャッシュからオブジェクトが返されません。 プリコンパイル済みクエリの詳細については、「<xref:System.Data.Linq.CompiledQuery>」および「[方法:クエリを格納および再利用する](how-to-store-and-reuse-queries.md)」を参照してください。  
  
 オブジェクトを ID キャッシュから取得するには、次に示す一般的な形式のいずれかでクエリを実行する必要があります。  
  
- <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
- <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 これらの一般的な形式では、`Function1`、`Function2`、および `predicate` が次のように定義されます。  
  
 `Function1` は、次のいずれかになります。  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` は、次のいずれかになります。  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` は、オブジェクトのプライマリ キー プロパティが定数値に設定された式である必要があります。 オブジェクトのプライマリ キーが複数のプロパティで定義されている場合は、それぞれのプライマリ キー プロパティが定数値に設定されている必要があります。 `predicate` に使用する必要がある形式の例を次に示します。  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>例  

 次のコードは、ID キャッシュからオブジェクトを取得する LINQ to SQL クエリの例です。  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [クエリの概念](query-concepts.md)
- [オブジェクト ID](object-identity.md)
- [背景情報](background-information.md)
- [オブジェクト ID](object-identity.md)
