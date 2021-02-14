---
description: '詳細情報: エンティティ コンテナー'
title: エンティティ コンテナー
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 1e90190e98ccf6bc6d48193adbe90a9ff31c4711
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672934"
---
# <a name="entity-container"></a>エンティティ コンテナー

"*エンティティ コンテナー*" は、[エンティティ セット](entity-set.md)、[アソシエーション セット](association-set.md)、および [関数インポート](model-declared-function.md)の論理グループです。  
  
 概念モデルで定義するエンティティ コンテナーは、次の条件を満たしている必要があります。  
  
- 1 つ以上のエンティティ コンテナーを各概念モデルに定義すること。  
  
- 各概念モデル内のエンティティ コンテナー名が一意であること。  
  
 エンティティ コンテナーは、1 つ以上の名前空間に定義されたエンティティ型またはアソシエーションを使用するエンティティ セットまたはアソシエーション セットを定義できます。 詳しくは、「[Entity Data Model: 名前空間](entity-data-model-namespaces.md)」をご覧ください。  
  
## <a name="example"></a>例  

 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  詳細については、次の例を参照してください。  
  
 ![3 種類のエンティティを持つモデルの例](./media/entity-container/example-model-three-entity-types.gif)  
  
 ダイアグラムにはエンティティ コンテナー情報が示されていませんが、概念モデルにはエンティティ コンテナーを定義する必要があります。 [ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれる DSL を使用して概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された概念モデルのエンティティ コンテナーを定義しています。 エンティティ コンテナー名は XML 属性に定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
