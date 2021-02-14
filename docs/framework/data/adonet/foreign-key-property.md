---
description: '詳細情報: 外部キーのプロパティ'
title: 外部キーのプロパティ
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 1666e4477c09dd5d0ed3d2c35a93ca21824e8a0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724129"
---
# <a name="foreign-key-property"></a>外部キーのプロパティ

Entity Data Model (EDM) における "*外部キーのプロパティ*" は、別の [エンティティ型](entity-type.md)の [エンティティ キー](entity-key.md)を含むエンティティ型のプリミティブ型の [プロパティ](property.md) (または一連のプリミティブ型のプロパティ) です。  
  
 外部キーのプロパティは、リレーショナル データベースの外部キー列に似ています。 リレーショナル データベースで外部キー列を使用してテーブル内の行の間のリレーションシップを作成するのと同様に、概念モデルでは外部キーのプロパティを使用してエンティティ型の間の[アソシエーション](association-type.md)を設定します。 エンティティ型の 1 つに外部キーのプロパティがある場合に、2 つのエンティティ型の間のアソシエーションを定義するには、[参照整合性制約](referential-integrity-constraint.md)を使用します。  
  
## <a name="example"></a>例  

 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。 `Book` エンティティ型には、`PublisherId` というプロパティがあります。`Publisher` アソシエーションに参照整合性制約を定義するときに、このプロパティは `PublishedBy` エンティティ型のエンティティ キーを参照します。  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "参照制約モデルの例")  
  
 [ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 次の CSDL は、外部キーのプロパティ `PublisherId` を使用して、上の概念モデルに示された `PublishedBy` アソシエーションに参照整合性制約を定義します。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
