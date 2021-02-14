---
description: '詳細情報: 仮想メンバー'
title: 仮想メンバー
ms.date: 10/22/2008
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 7618686764fb3a24ef53e5168b871366b7ffb5bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641786"
---
# <a name="virtual-members"></a>仮想メンバー

仮想メンバーはオーバーライドすることができ、それによってサブクラスの動作を変更することができます。 それらは、提供される機能拡張に関してコールバックとよく似ていますが、実行のパフォーマンスとメモリの消費に関してはそれよりも優れています。 また、仮想メンバーは、特別な種類の既存の型を作成 (特殊化) する必要があるシナリオでは、より自然に感じられます。

 仮想メンバーのパフォーマンスは、コールバックとイベントよりも優れていますが、非仮想メソッドほどは優れていません。

 仮想メンバーの主な欠点は、仮想メンバーの動作はコンパイル時にのみ変更できることです。 コールバックの動作は、実行時に変更できます。

 仮想メンバーは、コールバックのように (おそらくコールバック以上に)、設計、テスト、およびメンテナンスにコストがかかります。これは、仮想メンバーへのすべての呼び出しは予測不可能な方法でオーバーライドされ、任意のコードが実行される可能性があるためです。 また、仮想メンバーのコントラクトを明確に定義するには、通常はさらに多くの労力が必要であるため、それらを設計して文書化するコストが高くなります。

 ❌ メンバーを仮想にする正当な理由があり、かつ仮想メンバーの設計、テスト、およびメンテナンスに関連するすべてのコストを把握している場合を除いて、メンバーを仮想にしないでください。

 仮想メンバーは、互換性を損なわずに実行できる変更という観点から見ると、許容度が低くなっています。 また、ほとんどの場合、仮想メンバーへの呼び出しはインライン化されないため、非仮想メンバーよりも処理速度が遅くなります。

 ✔️ 絶対に必要な範囲にのみ、機能拡張を制限することを検討してください。

 ✔️ 仮想メンバーに対するアクセシビリティは、パブリックなものよりも保護されたものを優先してください。 パブリック メンバーは、保護された仮想メンバーを呼び出すことで (必要に応じて) 拡張性を提供する必要があります。

 クラスのパブリック メンバーは、そのクラスを直接使用するものに対して、適切な機能セットを提供する必要があります。 仮想メンバーはサブクラスでオーバーライドされるように設計されており、保護されたアクセシビリティは、すべての仮想拡張ポイントのスコープを、それらが使用できる場所に設定するための優れた方法です。

 *Portions &copy; 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [機能拡張のデザイン](designing-for-extensibility.md)
