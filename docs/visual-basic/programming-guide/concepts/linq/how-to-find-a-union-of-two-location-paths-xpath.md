---
title: '方法: 2 つのロケーション パスの和集合を検索する (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 36528d1748d5675231f14de92dcd78734a696711
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406873"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>方法: 2 つのロケーション パスの和集合を検索する (XPath-LINQ to XML) (Visual Basic)
XPath を使用すると、2 つの XPath ロケーション パスの結果の和集合を検索できます。  
  
 XPath 式を次に示します。  
  
 `//Category|//Price`  
  
 <xref:System.Linq.Enumerable.Concat%2A> 標準クエリ演算子を使用すると、同じ結果を得ることができます。  
  
## <a name="example"></a>例  
 この例では、`Category` 要素と `Price` 要素をすべて検索し、それらを 1 つのコレクションに連結します。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリで <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> を呼び出して、結果を並べ替えていることに注意してください。 XPath 式の評価結果もドキュメント順になります。  
  
 この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:数値データ (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md)」。  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```console
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a>関連項目

- [XPath ユーザー向けの LINQ to XML (Visual Basic)](linq-to-xml-for-xpath-users.md)
