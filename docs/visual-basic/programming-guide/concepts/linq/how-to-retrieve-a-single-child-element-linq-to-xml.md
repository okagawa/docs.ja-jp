---
title: '方法: 単一の子要素を取得する (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: ab28ddd960374b22f44ac0c8fc7bddfe0608b8c5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397844"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a>方法: 単一の子要素を取得する (LINQ to XML) (Visual Basic)
このトピックでは、子要素名を指定して単一の子要素を取得する方法について説明します。 子要素の名前が既知であり、この名前を持つ要素が 1 つしか存在しない場合は、コレクションの代わりに 1 つの要素だけを取得する方が便利な場合があります。  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> メソッドは、指定された <xref:System.Xml.Linq.XElement> を持つ最初の子 <xref:System.Xml.Linq.XName> を返します。  
  
 Visual Basic で単一の子要素を取得する場合の一般的な方法は、XML プロパティを使用し、配列インデクサー表記を使用して最初の要素を取得する方法です。  
  
## <a name="example"></a>例  
 <xref:System.Xml.Linq.XContainer.Element%2A> メソッドの使用例を次に示します。 この例では、`po` という名前の XML ツリーを受け取り、`Comment` という名前の最初の要素を検索します。  
  
 Visual Basic の例では、配列インデクサー表記を使用して単一の要素を取得しています。  
  
 この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:一般的な購買発注書 (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) を使用します。  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>例  
 上記と同じコードを使用して、名前空間内の XML から要素を取得する例を次に示します。 詳細については、「[名前空間の概要 (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)」を参照してください。  
  
 この例では、次の XML ドキュメントを使用します: [サンプル XML ファイル: 名前空間内の一般的な購買発注書](sample-xml-file-typical-purchase-order-in-a-namespace.md)を使用します。  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>関連項目

- [LINQ to XML 軸 (Visual Basic)](linq-to-xml-axes.md)
