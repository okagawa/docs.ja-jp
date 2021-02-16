---
description: '詳細情報: 方法:XML 子要素にアクセスする (Visual Basic)'
title: '方法: XML 子要素にアクセスする'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: fad4d45853006762bc319b0ff8f9143ef13058da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433240"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>方法: XML 子要素にアクセスする (Visual Basic)

この例では、子軸プロパティを使用して、XML 要素内で指定した名前を持つすべての XML 子要素にアクセスする方法を示しています。 特に、<xref:System.Xml.Linq.XElement.Value%2A> プロパティを使用して、`name` 子軸プロパティによって返されるコレクション内の最初の要素の値を取得します。 子軸プロパティ `name` では、`contact` オブジェクト内の `phone` という名前のすべての子要素を取得します。 また、この例では、`phone` 子軸プロパティを使用して、`contact` オブジェクトに含まれている `phone` という名前のすべての子要素にアクセスしています。  
  
## <a name="example"></a>例  

 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  

 この例で必要な要素は次のとおりです。  
  
- <xref:System.Xml.Linq> 名前空間への参照  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [XML 子軸プロパティ](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [XML Value プロパティ](../../../language-reference/xml-axis/xml-value-property.md)
- [Visual Basic での XML へのアクセス](accessing-xml.md)
- [XML](index.md)
