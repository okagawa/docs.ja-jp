---
title: XmlSchemaSet による XML スキーマ (XSD) 検証
description: .NET で XmlSchemaSet クラスを使用して、XML スキーマ定義言語 (XSD) スキーマに対して XML ドキュメントを検証する方法について学習します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 9e1d4b7e8c805436c32d2ae7b340ee251741f4a1
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824572"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>XmlSchemaSet による XML スキーマ (XSD) 検証

XML ドキュメントは、<xref:System.Xml.Schema.XmlSchemaSet> の XML スキーマ定義言語 (XSD) スキーマを基準として検証できます。  
  
## <a name="validate-xml-documents"></a>XML ドキュメントの検証  
 XML ドキュメントは、<xref:System.Xml.XmlReader.Create%2A> クラスの <xref:System.Xml.XmlReader> メソッドを使用して検証します。 XML ドキュメントを検証するには、XML ドキュメントの検証に使用する XML スキーマ定義言語 (XSD) スキーマを持つ <xref:System.Xml.XmlReaderSettings> オブジェクトを作成します。  
  
> [!NOTE]
> <xref:System.Xml.Schema> 名前空間には、[LINQ to XML (C#)](../../linq/linq-xml-overview.md) や [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md) を使用しているときに XSD ファイルに対する XML ツリーの検証を容易にする拡張メソッドが含まれています。 LINQ to XML を使用した XML ドキュメントの検証に関する詳細については、「[XSD を使用して検証する方法 (LINQ to XML) (C#)](../../linq/validate-xsd.md)」および「[方法: XSD を使用して検証する (LINQ to XML) (Visual Basic)](../../linq/validate-xsd.md)」を参照してください。
  
 独立したスキーマまたはスキーマのセット (<xref:System.Xml.Schema.XmlSchemaSet> を使用) を <xref:System.Xml.Schema.XmlSchemaSet> に追加するには、そのどちらかを <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドにパラメーターとして渡します。 ドキュメントを検証する際には、ドキュメントの対象名前空間がスキーマ セット内のスキーマの対象名前空間と一致している必要があります。  
  
 XML ドキュメントのサンプルを次に示します。  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 XML ドキュメントのサンプルを検証するスキーマを次に示します。  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 以下のコード サンプルでは、<xref:System.Xml.XmlReaderSettings> オブジェクトの <xref:System.Xml.XmlReaderSettings.Schemas%2A> プロパティに上記のスキーマが追加されます。 <xref:System.Xml.XmlReaderSettings> オブジェクトは、上記の XML ドキュメントを検証する <xref:System.Xml.XmlReader.Create%2A> オブジェクトの <xref:System.Xml.XmlReader> メソッドにパラメーターとして渡されます。  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> オブジェクトの <xref:System.Xml.XmlReaderSettings> プロパティが `Schema` に設定されて、<xref:System.Xml.XmlReader.Create%2A> オブジェクトの <xref:System.Xml.XmlReader> メソッドによる XML ドキュメントの検証が行われます。 XML のドキュメントおよびスキーマの検証中に発見されたエラーによって発生する <xref:System.Xml.Schema.ValidationEventHandler> イベントまたは <xref:System.Xml.XmlReaderSettings> イベントを処理するために、<xref:System.Xml.Schema.XmlSeverityType.Warning> オブジェクトに <xref:System.Xml.Schema.XmlSeverityType.Error> を追加します。  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [スキーマをコンパイルするための XmlSchemaSet](xmlschemaset-for-schema-compilation.md)
- [XML スキーマの使用](working-with-xml-schemas.md)
