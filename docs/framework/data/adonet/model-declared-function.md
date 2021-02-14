---
description: '詳細情報: モデル宣言関数'
title: モデル宣言関数
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: c9a5cedb8c9706aa0d299635f60f762b92ca6d78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786265"
---
# <a name="model-declared-function"></a>モデル宣言関数

"*モデル宣言関数*" は、概念モデルで宣言されていても、その概念モデルには定義されていない関数です。 この関数は、ホスト環境またはストレージ環境で定義します。 たとえば、モデル宣言関数は、データベースに定義された関数にマップされ、これによって概念モデルにおけるサーバー側の機能が公開される場合があります。  
  
 モデル宣言関数の宣言には、次の情報が含まれます。  
  
- 関数の名前。 (必須)  
  
- 戻り値の型。 (オプション)。  
  
    > [!NOTE]
    > 戻り値が指定されていない場合、戻り値の型は void になります。  
  
- パラメーター名と型を含むパラメーター情報。 (オプション)。  
  
## <a name="example"></a>例  

 [ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 CSDL には、モデル宣言関数の 1 つの実装手段として、関数インポートがあります ([FunctionImport 要素](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)を使用します)。 次の CSDL は、関数インポート定義を含むエンティティ コンテナーを定義しています。 戻り値の型が指定されていないため、関数の戻り値の型は void になります。  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
