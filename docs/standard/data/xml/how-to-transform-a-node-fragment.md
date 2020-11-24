---
title: '方法: ノード フラグメントを変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: 5c69a35497feced92a05e124307d3be584ab86b7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829441"
---
# <a name="how-to-transform-a-node-fragment"></a>方法: ノード フラグメントを変換する
<xref:System.Xml.XmlDocument> オブジェクトまたは <xref:System.Xml.XPath.XPathDocument> オブジェクトに含まれるデータを変換すると、XSLT 変換はドキュメント全体に適用されます。 つまり、ドキュメント ルート ノード以外のノードを指定しても、変換処理では、読み込んだドキュメントのすべてのノードがアクセスされます。 1 つのノード フラグメントを変換するには、ノード フラグメントだけを含むオブジェクトを別に作成し、そのオブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。  
  
## <a name="procedures"></a>プロシージャ  
  
#### <a name="to-transform-a-node-fragment"></a>1 つのノード フラグメントを変換するには  
  
1. ソース ドキュメントを含むオブジェクトを作成します。  
  
2. 変換するノード フラグメントを見つけます。  
  
3. そのノード フラグメントだけの別のオブジェクトを作成します。  
  
4. ノード フラグメントを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。  
  
## <a name="example"></a>例  
 次の例は、1 つのノード フラグメントを変換して、結果をコンソールに出力します。  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>入力  
  
##### <a name="booksxml"></a>books.xml  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>single.xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Output  
 Book title is The Confidence Man.  
  
## <a name="see-also"></a>関連項目

- [XslCompiledTransform クラスの使用](using-the-xslcompiledtransform-class.md)
