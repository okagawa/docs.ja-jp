---
title: エンティティ セット
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 5a2465801c270813dd7bca2144d05fa202571153
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738424"
---
# <a name="entity-set"></a>エンティティ セット
"*エンティティ セット*" は、[エンティティ型](entity-type.md)のインスタンスと、そのエンティティ型から派生するあらゆる型のインスタンスの論理コンテナーです。 (派生型について詳しくは、「[Entity Data Model: 継承](entity-data-model-inheritance.md)」をご覧ください。)エンティティ型とエンティティ セットの間のリレーションシップは、リレーショナル データベースの行とテーブルの間のリレーションシップと似ています。エンティティ型では、行のようにデータの構造が記述され、エンティティ セットには、テーブルのように特定の構造のインスタンスが含まれます。 エンティティ セットは、データ モデリング構造ではなく、データ構造を表しません。 エンティティ セットは、エンティティ型のインスタンスをグループ化してデータ ストアにマップするための、ホスト環境またはストレージ環境 (共通言語ランタイムや SQL Server データベースなど) の構造を提供します。  
  
 エンティティ セットは、エンティティ セットと[アソシエーション セット](association-set.md)の論理グループである[エンティティ コンテナー](entity-container.md)内で定義されます。  
  
 エンティティ型のインスタンスがエンティティ セット内に存在できるようにするには、次の条件を満たしている必要があります。  
  
- インスタンスの型がエンティティ セットの基本になるエンティティ型と同じであるか、インスタンスの型がエンティティ型のサブタイプであること。  
  
- インスタンスの[エンティティ キー](entity-key.md)がエンティティ セット内で一意であること。  
  
- インスタンスが他のエンティティ セットに存在しないこと。  
  
    > [!NOTE]
    > 同じエンティティ型を使用して複数のエンティティ セットを定義できますが、特定のエンティティ型のインスタンスは、1 つのエンティティ セット内のみに存在できます。  
  
 概念モデルの各エンティティ型にはエンティティ セットを定義する必要がありません。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  
  
 ![3 種類のエンティティを持つモデルの例](./media/entity-set/example-model-three-entity-types.gif)  
  
 次のダイアグラムには、上の概念モデルに基づく 2 つのエンティティ セット (`Books` および `Publishers`) と、アソシエーション セット(`PublishedBy`) を示しています。 `Books` エンティティ セット内の Bi は、実行時の `Book` エンティティ型インスタンスを表します。 同様に、Pj は、`Publishers` エンティティ セットの `Publisher` インスタンスを表します。 BiPj は、`PublishedBy` アソシエーション セット内にある `PublishedBy` アソシエーションのインスタンスを表します。  
  
 ![セットの例を示すスクリーンショット。](./media/entity-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 次の CSDL は、上の概念モデルに示された各エンティティ型に対して 1 つのエンティティ セットを持つエンティティ コンテナーを定義しています。 各エンティティ セットの名前とエンティティ型は、XML 属性で定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 型ごとに複数のエンティティ セット (Multiple-Entity-Sets-per-Type: MEST) を定義できます。 次の CSDL は、`Book` エンティティ型のエンティティ セットを 2 つ持つエンティティ コンテナーを定義しています。  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
