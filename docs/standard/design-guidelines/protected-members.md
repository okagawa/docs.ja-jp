---
description: '詳細情報: プロテクト メンバー'
title: プロテクト メンバー
ms.date: 10/22/2008
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 5860828a5a469c77fbee001d01460a488fda4edf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731761"
---
# <a name="protected-members"></a>プロテクト メンバー

プロテクト メンバー自体では拡張機能は提供されませんが、サブクラス化による拡張性をいっそう強力にすることができます。 それらを使用すると、メインのパブリック インターフェイスを不必要に複雑にすることなく、高度なカスタマイズ オプションを公開できます。

 フレームワーク デザイナーは、"プロテクト" という名前からセキュリティに関して誤った認識を持つ可能性があるため、プロテクト メンバーには注意する必要があります。 だれでも、アンシールド クラスをサブクラス化し、プロテクト メンバーにアクセスできるので、パブリック メンバーに使用されるものと同じ防御的なコーディング方法がすべてプロテクト メンバーに適用されます。

 ✔️ 高度なカスタマイズには、プロテクト メンバーの使用を検討します。

 ✔️ セキュリティ、ドキュメント、互換性分析の目的では、アンシールド クラスのプロテクト メンバーをパブリックとして扱います。

 だれでもクラスを継承し、プロテクト メンバーにアクセスできます。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [機能拡張のデザイン](designing-for-extensibility.md)
