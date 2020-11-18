---
title: 機能拡張のデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 9e75ef433f3bd9af34e8dd40331a8267755e59fe
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821386"
---
# <a name="designing-for-extensibility"></a>機能拡張のデザイン
フレームワークを設計する際の重要な要素の1つは、フレームワークの拡張性が慎重に考慮されていることです。 これには、さまざまな拡張メカニズムに関連するコストと利点を理解する必要があります。 この章では、拡張メカニズム (サブクラス化、イベント、仮想メンバー、コールバックなど) を、フレームワークの要件を最もよく満たすことができるかどうかを判断するのに役立ちます。  
  
 フレームワークで拡張性を実現するには、さまざまな方法があります。 これは、あまり強力ではなく、コストが非常に高く、非常にコストが高くなります。 特定の拡張要件については、要件を満たす最もコストの低い拡張性メカニズムを選択する必要があります。 通常は、後で拡張機能を追加できることに注意してくださいが、重大な変更を導入しなくても、この機能を使用することはできません。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [シールされていないクラス](unsealed-classes.md)  
 [プロテクトメンバー](protected-members.md)  
 [イベントとコールバック](events-and-callbacks.md)  
 [仮想メンバー](virtual-members.md)  
 [抽象化 (抽象型とインターフェイス)](abstractions-abstract-types-and-interfaces.md)  
 [抽象化を実装するための基本クラス](base-classes-for-implementing-abstractions.md)  
 [シール](sealing.md)  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワークデザインのガイドライン](index.md)
