---
title: '方法: XML リテラルに式を埋め込む'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 59ba03be6e132203523427d3b7af5a163b6f05ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392315"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>方法: XML リテラルに式を埋め込む (Visual Basic)
XML リテラルと埋め込み式を組み合わせて、実行時に作成される内容を含む XML ドキュメント、フラグメント、または要素を作成できます。 次の例では、埋め込み式を使用して、実行時に要素の内容、属性、および要素名を設定する方法を示します。  
  
 埋め込み式の構文は `<%=` `exp` `%>` となります。これは ASP.NET で使用される構文と同じです。 詳細については、「[XML での埋め込み式](embedded-expressions-in-xml.md)」を参照してください。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API を使用して、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] オブジェクトを作成することもできます。 詳細については、「<xref:System.Xml.Linq.XElement>」を参照してください。  
  
## <a name="procedures"></a>プロシージャ  
  
#### <a name="to-insert-text-as-element-content"></a>要素の内容としてテキストを挿入するには  
  
- 次の例は、名前の開始要素と終了要素の間に `contactName` 変数に含まれるテキストを挿入する方法を示しています。  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     この例を実行すると、次の出力が生成されます。  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>属性値としてテキストを挿入するには  
  
- 次の例は、`phoneType` 変数に含まれるテキストを `type` 属性の値として挿入する方法を示しています。  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     この例を実行すると、次の出力が生成されます。  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>要素名のテキストを挿入するには  
  
- 次の例は、`elementName` 変数に含まれるテキストを要素の名前として挿入する方法を示しています。  
  
     この手法を使用して要素を作成する場合は、\</> タグで終了する必要があります。  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     この例を実行すると、次の出力が生成されます。  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>関連項目

- [方法: XML リテラルを作成する](how-to-create-xml-literals.md)
- [XML での埋め込み式](embedded-expressions-in-xml.md)
- [Visual Basic での XML の作成](creating-xml.md)
- [XML](index.md)
