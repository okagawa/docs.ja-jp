---
title: XML ドキュメント オブジェクト モデル (DOM) の階層構造
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: a6099b6c5e30fbf2e4d5d4ed046369bc8f884845
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291436"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>XML ドキュメント オブジェクト モデル (DOM) の階層構造
XML ドキュメント オブジェクト モデル (DOM) のクラスの階層構造を次の図に示します。クラス名に続くかっこ内の名前は、W3C (World Wide Web Consortium) 名です。  
  
 ![XML ドキュメント オブジェクト モデル &#40;DOM&#41; の階層構造](media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
XML ドキュメント オブジェクト モデル (DOM) の階層構造  
  
 次のクラスは **XmlNode** から継承したものではありません。  
  
- **XmlImplementation**  
  
- **XmlNamedNodeMap**  
  
- **XmlNodeList**  
  
- **XmlNodeChangedEventArgs**  
  
 **XmlImplementation** クラスは、XML ドキュメントを作成するために使われます。 詳細については、「[XML ドキュメントの作成](xml-document-creation.md)」を参照してください。  
  
 **XmlNamedNodeMap** クラスは、順序付けられていないノード セットを処理します。 詳細については、「[名前またはインデックスによる順序付けられていないノードの取得](unordered-node-retrieval-by-name-or-index.md)」を参照してください。  
  
 **XmlNodeList** クラスは、順序付けられたノード リストを処理します。 詳細については、「[インデックスによる順序付けられたノードの取得](ordered-node-retrieval-by-index.md)」を参照してください。  
  
 **XmlNodeChangedEventArgs** クラスは、**XmlDocument** に登録されたイベント ハンドラーを処理します。 詳細については、「[XmlNodeChangedEventArgs による XML ドキュメントのイベント処理](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)」を参照してください。  
  
 **XmlLinkedNode** クラスは **XmlNode** から継承しています。 その目的は、**XmlNode** の **PreviousSibling** と **NextSibling** という 2 つのメソッドをオーバーライドすることです。 これらのオーバーライドされたメソッドは、前後に兄弟を持つ **XmlCharacterData**、**XmlDeclaration**、**XmlDocumentType**、**XmlElement**、**XmlEntityReference**、**XmlProcessingInstruction** クラスによって継承され、使用されます。  
  
## <a name="see-also"></a>関連項目

- [XML ドキュメント オブジェクト モデル (DOM)](xml-document-object-model-dom.md)
