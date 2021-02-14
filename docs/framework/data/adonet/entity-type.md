---
description: '詳細情報: エンティティ型'
title: エンティティ型
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: fb801ca8565fce01466f30bddc8c14c39af568c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724363"
---
# <a name="entity-type"></a>エンティティ型

"*エンティティ型*" は、Entity Data Model (EDM) でデータ構造を記述するために不可欠な構成要素です。 概念モデルでのエンティティ型は、顧客や注文のように、トップレベル概念の構造を表します。 エンティティ型は、エンティティ型のインスタンスのテンプレートです。 各テンプレートには、次の情報が含まれています。  
  
- 一意の名前  (必須)   
  
- 1 つ以上のプロパティにより定義される[エンティティ キー](entity-key.md)。 (必須)   
  
- [プロパティ](property.md)の形式のデータ。 (省略可能)   
  
- [アソシエーション](association-type.md)の 1 つの [End](association-end.md) から別の End へのナビゲーションを可能にする[ナビゲーション プロパティ](navigation-property.md)。 (オプション)。  
  
 アプリケーションでは、エンティティ型のインスタンスが特定のオブジェクト (特定の顧客や注文など) を表します。 エンティティ型の各インスタンスに対して、[エンティティ セット](entity-set.md)内の[エンティティ キー](entity-key.md)を一意にする必要があります。  
  
 2 つのエンティティ型のインスタンスは、型が同じであり、エンティティ キーの値が等しい場合にのみ、等価のインスタンスと見なされます。  
  
## <a name="example"></a>例  

 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  
  
 ![3 種類のエンティティを持つモデルの例](./media/entity-type/example-model-three-entity-types.gif)  
  
 各エンティティ型のエンティティ キーを構成するプロパティには、"(キー)" と示されています。  
  
 [ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義しています。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
- [facet](facet.md)
