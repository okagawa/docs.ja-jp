---
description: '詳細情報: 抽象化 (抽象型およびインターフェイス)'
title: 抽象化 (抽象型およびインターフェイス)
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
ms.openlocfilehash: 8dc82f004d655429e842c63fab4defff0fd74ab2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642442"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>抽象化 (抽象型およびインターフェイス)

抽象化はコントラクトを記述する型ですが、コントラクトの完全な実装は提供しません。 抽象化は通常、抽象クラスまたは抽象インターフェイスとして実装され、付属する適切に定義された一連の参照ドキュメントで、コントラクトを実装する型の必要なセマンティクスが説明されています。 .NET Framework の最も重要な抽象化は、<xref:System.IO.Stream>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Object> などです。

 抽象化のコントラクトをサポートする具象型を実装し、抽象化を使用する (操作する) フレームワーク API でこの具象型を使用することにより、フレームワークを拡張できます。

 時が経っても変わらずに意味があり有用な抽象化を設計することは、非常に困難です。 最も難しいのは、多すぎも少なすぎもしない適切なメンバーのセットを作成することです。 抽象化のメンバーが多すぎると、実装が困難になるか、不可能になることさえあります。 約束された機能に対してメンバーが少なすぎると、多くの興味深いシナリオで役に立たなくなります。

 フレームワークの抽象化が多すぎても、フレームワークの使いやすさに悪影響を及ぼします。 多くの場合、抽象化が基になっている具象実装と API の全体像に抽象化がどのように当てはまるのかを理解しないで抽象化を理解することは、非常に困難です。 また、抽象化とそのメンバーの名前はどうしても抽象的になるので、それらが使用される広範なコンテキストを最初に理解してからでないと、わかりにくく使いづらいことがよくあります。

 ただし、抽象化によって提供される非常に強力な拡張性は、多くの場合、他の拡張メカニズムでは実現できません。 それらは、プラグイン、制御の反転 (IoC)、パイプラインなど、多くのアーキテクチャ パターンの中核になるものです。 また、それらはフレームワークのテストの容易性にとっても極めて重要です。 適切に抽象化されていると、単体テストのために多くの依存関係をスタブ化できます。 まとめると、抽象化は、最新のオブジェクト指向フレームワークで求められる豊富な機能の鍵を握るものです。

 ❌ 抽象化を使用するいくつかの具象実装と API を開発することによってテストしてからでない限り、抽象化を提供しないでください。

 ✔️ 抽象化を設計するときは、抽象クラスにするかインターフェイスにするかを慎重に選択します。

 ✔️ 抽象化の具象実装のために参照テストを提供することを検討します。 そのようなテストがあると、ユーザーは実装でコントラクトが正しく実装されているかどうかをテストできます。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [機能拡張のデザイン](designing-for-extensibility.md)
