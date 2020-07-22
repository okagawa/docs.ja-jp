---
title: シリアル化時の空白の維持 2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: e9b73089830bf7e6cb0ea9e469bf667f12c571d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396403"
---
# <a name="preserving-white-space-while-serializing"></a>シリアル化時の空白の維持
このトピックでは、XML ツリーをシリアル化するときに空白を制御する方法について説明します。  
  
 一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。 書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。 これが [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の既定の動作です。  
  
 もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。 場合によっては、このインデントを一切変更しないようにする必要があります。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>XML ツリーをシリアル化するメソッドの空白に関する動作  
 <xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq.XDocument> クラスにある次のメソッドは、XML ツリーをシリアル化します。 XML ツリーは、ファイル、<xref:System.IO.TextReader>、または <xref:System.Xml.XmlReader> にシリアル化できます。 `ToString` メソッドは、文字列にシリアル化します。  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取らない場合は、シリアル化された XML が書式設定 (インデント) されます。 この場合、XML ツリー内の意味のない空白はすべて破棄されます。  
  
 メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取る場合は、シリアル化された XML が書式設定 (インデント) されないことを指定できます。 この場合、XML ツリー内の空白はすべて維持されます。  
  
## <a name="see-also"></a>関連項目

- [XML ツリーのシリアル化 (Visual Basic)](serializing-xml-trees.md)
