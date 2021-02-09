---
description: '詳細情報: 方法:主キーを表す'
title: '方法: 主キーを表す'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 1fbac2d60bd730718b5330bfd48910a61deae15c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723609"
---
# <a name="how-to-represent-primary-keys"></a>方法: 主キーを表す

データベース列の主キーを表すプロパティまたはフィールドを指定するには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性の <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> プロパティを使用します。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>」を参照してください。  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、計算列は主キーとしてサポートされません。  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>プロパティまたはフィールドを主キーとして指定するには  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2. 値として `true` を指定します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL オブジェクト モデル](the-linq-to-sql-object-model.md)
- [方法: コード エディターを使用してエンティティ クラスをカスタマイズする](how-to-customize-entity-classes-by-using-the-code-editor.md)
