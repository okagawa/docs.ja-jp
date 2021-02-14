---
description: '詳細情報: System.Xml の使用法'
title: System.Xml の使用法
ms.date: 10/22/2008
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 51886c07f0b68bb329c258daa93e809d94839341
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641851"
---
# <a name="systemxml-usage"></a>System.Xml の使用法

このセクションでは、<xref:System.Xml?displayProperty=nameWithType> 名前空間に存在するさまざまな型で、XML データを表すために使用できる型の使用方法について説明します。

 ❌ XML データを表すために <xref:System.Xml.XmlNode> または <xref:System.Xml.XmlDocument> を使用しないでください。 代わりに、<xref:System.Xml.XPath.IXPathNavigable>、<xref:System.Xml.XmlReader>、または <xref:System.Xml.XmlWriter> のインスタンス、または <xref:System.Xml.Linq.XNode> のサブタイプを優先的に使用してください。 `XmlNode` と `XmlDocument` は、パブリック API に公開するように設計されていません。

 ✔️ XML を受け入れるか返すメンバーの入力または出力として、`XmlReader`、`IXPathNavigable`、または `XNode` のサブタイプを使用してください。

 これらの抽象化を、`XmlDocument`、`XmlNode`、または <xref:System.Xml.XPath.XPathDocument> の代わりに使用してください。これにより、メモリ内 XML ドキュメントの特定の実装からメソッドが切り離され、`XNode`、`XmlReader`、または <xref:System.Xml.XPath.XPathNavigator> を公開する仮想 XML データ ソースとの連携が可能になります。

 ❌ 基になるオブジェクト モデルまたはデータ ソースの XML ビューを表す型を作成する場合に、`XmlDocument` をサブクラス化しないでください。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [使用方法のガイドライン](usage-guidelines.md)
