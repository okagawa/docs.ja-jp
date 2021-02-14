---
description: '詳細情報: インターフェイスのデザイン'
title: インターフェイスのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 387f921f8bdbe6c6d398aa31dcc8a22c7da455f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641981"
---
# <a name="interface-design"></a>インターフェイスのデザイン

ほとんどの API はクラスと構造体を使用して最良のモデル化が行われますが、インターフェイスのほうが適している場合や、インターフェイスが唯一のオプションである場合があります。

 CLR では複数の継承はサポートされていません (つまり、複数の基底クラスから CLR クラスを継承することはできません) が、１ つの基底クラスからの継承に加えて、型で 1 つまたは複数のインターフェイスを実装できます。 したがって、多くの場合、インターフェイスは、多重継承の効果を実現するために使用されます。 たとえば、<xref:System.IDisposable> は、参加する必要のある他の継承階層とは無関係に、型で廃棄性をサポートできるようにするインターフェイスです。

 インターフェイスを定義することが適している他の状況としては、いくつかの値型を含む複数の型によってサポートされることが可能な共通インターフェイスを作成することがあります。 値型は <xref:System.ValueType> 以外の型から継承することはできませんが、インターフェイスを実装することはできるため、インターフェイスを使用することが共通の基本データ型を提供するための唯一のオプションになります。

 ✔️ 値型を含む型セットによってサポートされる何らかの共通 API が必要な場合は、インターフェイスを定義してください。

 ✔️ 他の型から既に継承されている型に対してインターフェイスの機能をサポートする必要がある場合は、インターフェイスを定義することを検討してください。

 ❌ マーカー インターフェイス (メンバーのないインターフェイス) を使用することは避けてください。

 クラスを特定の特性 (マーカー) を持っているとマークする必要がある場合は、通常は、インターフェイスではなくカスタム属性を使用してください。

 ✔️ インターフェイスの実装である型を少なくとも 1 つ用意してください。

 これを行うと、インターフェイスの設計を検証するのに役立ちます。 たとえば、<xref:System.Collections.Generic.List%601> は <xref:System.Collections.Generic.IList%601> インターフェイスの実装です。

 ✔️ 定義した各インターフェイスを使用する API (インターフェイスをパラメーターとして使用するメソッドまたはインターフェイスと型指定されたプロパティ) を少なくとも 1 つ用意してください。

 これを行うと、インターフェイスの設計を検証するのに役立ちます。 たとえば、<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> では <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> インターフェイスが使用されます。

 ❌ 以前に出荷されているインターフェイスにメンバーを追加しないでください。

 これを行うと、インターフェイスの実装が中断されます。 バージョンの問題を回避するために、新しいインターフェイスを作成してください。

 これらのガイドラインで説明されている状況を除き、一般に、マネージド コードの再利用可能なライブラリの設計では、インターフェイスではなくクラスを選択してください。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](type.md)
- [フレームワーク デザインのガイドライン](index.md)
