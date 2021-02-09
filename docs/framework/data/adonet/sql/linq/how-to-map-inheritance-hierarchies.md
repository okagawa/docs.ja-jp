---
description: '詳細情報: 方法:継承階層を割り当てる'
title: '方法: 継承階層を割り当てる'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 19d7e73dd477a474c98612fae8b0376188d1f08f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802035"
---
# <a name="how-to-map-inheritance-hierarchies"></a>方法: 継承階層を割り当てる

LINQ で継承の割り当てを実装するには、以下の手順で示すように、継承階層のルート クラスで属性および属性プロパティを指定する必要があります。 Visual Studio を使用している開発者は、オブジェクト リレーショナル デザイナーを使用して継承改装をマップできます。 「[方法:O/R デザイナーを使用して継承を構成する](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)」を参照してください。  
  
> [!NOTE]
> サブクラスには特別な属性やプロパティは必要ありません。 特に、サブクラスに <xref:System.Data.Linq.Mapping.TableAttribute> 属性がない点に注意してください。  
  
### <a name="to-map-an-inheritance-hierarchy"></a>継承階層を割り当てるには  
  
1. ルート クラスに <xref:System.Data.Linq.Mapping.TableAttribute> 属性を追加します。  
  
2. ルート クラスに対し、階層構造の各クラスについて <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性を追加します。  
  
3. 各 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性に対し、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> プロパティを定義します。  
  
     このプロパティは、データベース テーブルの <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 列に含まれる値を保持し、このデータ行が属するクラスまたはサブクラスを示します。  
  
4. 各 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性に対し、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> プロパティも追加します。  
  
     このプロパティは、キー値が示すクラスまたはサブクラスを表す値を保持します。  
  
5. 1 つの <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性にのみ、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> プロパティを追加します。  
  
     このプロパティでは、データベース テーブルから取得された識別値が、継承マッピングのどの <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 値とも一致しないときの、"*フォールバック*" マッピングが指定されます。  
  
6. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
     このプロパティは、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 値を保持する列であることを示します。  
  
## <a name="example"></a>例  
  
> [!NOTE]
> Visual Studio を使用している場合は、オブジェクト リレーショナル デザイナーを使用して、継承を構成できます。 「[方法:O/R デザイナーを使用して継承を構成する](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 次のコード例では、`Vehicle` がルート クラスとして定義され、LINQ の階層を記述するためにここまでの手順が実装されています。  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [継承のサポート](inheritance-support.md)
- [方法: コード エディターを使用してエンティティ クラスをカスタマイズする](how-to-customize-entity-classes-by-using-the-code-editor.md)
