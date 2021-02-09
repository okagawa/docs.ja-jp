---
description: '詳細情報: XSD としての DataSet スキーマ情報の書き込み'
title: XSD としての DataSet スキーマ情報の書き込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: e05188c74ca21e73ee5151da817e143102640a13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651354"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>XSD としての DataSet スキーマ情報の書き込み

<xref:System.Data.DataSet> のスキーマを XML スキーマ定義言語 (XSD) スキーマとして書き込むと、このスキーマを XML ドキュメントに転送できます。このとき関連データを含む定義、または関連データを含まない定義ができます。 XML スキーマはファイル、ストリーム、<xref:System.Xml.XmlWriter>、または文字列に書き込むことができるため、厳密に型指定された **DataSet** を生成するときに役立ちます。 厳密に型指定された **DataSet** オブジェクトの詳細については、「[型指定されたデータセット](typed-datasets.md)」を参照してください。  
  
 テーブルの列を XML スキーマで表す方法を指定するには、<xref:System.Data.DataColumn> オブジェクトの **ColumnMapping** プロパティを使用します。 詳細については、「[DataSet 内容の XML データとしての書き込み](writing-dataset-contents-as-xml-data.md)」の「XML 要素、属性、およびテキストへの列の割り当て」を参照してください。  
  
 **DataSet** のスキーマを XML スキーマとしてファイル、ストリーム、または **XmlWriter** に書き込むには、**DataSet** の **WriteXmlSchema** メソッドを使用します。 **WriteXmlSchema** は、XML スキーマの書き込み先を指定するパラメーターを 1 つ受け取ります。 次のコード例では、ファイル名が含まれる文字列と <xref:System.IO.StreamWriter> オブジェクトを渡して **DataSet** の XML スキーマをファイルに書き込む方法を示します。  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 **DataSet** のスキーマを取得し、XML スキーマ文字列として書き込むには、次の例に示すように、**GetXmlSchema** メソッドを使用します。  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>関連項目

- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [DataSet 内容の XML データとしての書き込み](writing-dataset-contents-as-xml-data.md)
- [型指定されたデータセット](typed-datasets.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET の概要](../ado-net-overview.md)
