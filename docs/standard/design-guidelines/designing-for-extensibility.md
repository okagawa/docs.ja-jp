---
description: '詳細情報: 機能拡張のデザイン'
title: 機能拡張のデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 148ae25380698a5a1161fb9fbdd3cc60102e865d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642267"
---
# <a name="designing-for-extensibility"></a>機能拡張のデザイン

フレームワークを設計するときに重要な点の 1 つは、フレームワークの拡張性を慎重に考慮することです。 これには、さまざまな拡張メカニズムに関連するコストと利点を理解する必要があります。 この章は、どの拡張メカニズム (サブクラス化、イベント、仮想メンバー、コールバックなど) が自分のフレームワークの要件に最適かを判断するのに役立ちます。  
  
 フレームワークで拡張性を実現するには、さまざまな方法があります。 これは、非力でも低コストのものから、強力でも高コストのものまでさまざまです。 特定の拡張要件について、要件を満たす最も低コストの拡張性メカニズムを選択する必要があります。 通常、後で拡張機能を追加することはできますが、破壊的変更を発生させずにそれを取り除くことはできないことに注意してください。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [シールされていないクラス](unsealed-classes.md)  
 [プロテクト メンバー](protected-members.md)  
 [イベントとコールバック](events-and-callbacks.md)  
 [仮想メンバー](virtual-members.md)  
 [抽象化 (抽象型およびインターフェイス)](abstractions-abstract-types-and-interfaces.md)  
 [抽象化の実装用の基本クラス](base-classes-for-implementing-abstractions.md)  
 [シール](sealing.md)  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
