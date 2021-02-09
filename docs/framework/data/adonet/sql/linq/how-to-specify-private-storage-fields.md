---
description: '詳細情報: 方法:プライベート ストレージ フィールドを指定する'
title: '方法: プライベート ストレージ フィールドを指定する'
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: 09f3566ca85a69f27794329ae12fc45d88bb518c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785901"
---
# <a name="how-to-specify-private-storage-fields"></a>方法: プライベート ストレージ フィールドを指定する

基になるストレージ フィールドの名前を指定するには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Mapping.DataAttribute> 属性の <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> プロパティを使用します。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>」を参照してください。  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a>基になるストレージ フィールドの名前を指定するには  
  
1. <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2. フィールドの名前を <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> プロパティの値として代入します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL オブジェクト モデル](the-linq-to-sql-object-model.md)
- [方法: コード エディターを使用してエンティティ クラスをカスタマイズする](how-to-customize-entity-classes-by-using-the-code-editor.md)
