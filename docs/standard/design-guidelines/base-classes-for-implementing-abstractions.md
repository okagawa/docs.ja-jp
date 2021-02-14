---
description: '詳細情報: 抽象化の実装用の基本クラス'
title: 抽象化の実装用の基本クラス
ms.date: 10/22/2008
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: 255891695583e36977663153b0ccac98b7fff4c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642345"
---
# <a name="base-classes-for-implementing-abstractions"></a>抽象化の実装用の基本クラス

厳密に言えば、クラスは、それから別のクラスが派生しているときは基底クラスになります。 ただし、このセクションで基底クラスといった場合は、主に、共通の抽象化を提供すること、または他のクラスが継承を通して既定の実装を再利用することを目的として設計されたクラスのことです。 基底クラスは、通常、継承の階層において、階層のルートにある抽象化と、下端にある複数のカスタム実装の間の、中間に位置します。

 それらは、抽象化を実装するための実装ヘルパーとして機能します。 たとえば、順序付けられた項目のコレクションに対するフレームワークの抽象化の 1 つは、<xref:System.Collections.Generic.IList%601> インターフェイスです。 <xref:System.Collections.Generic.IList%601> の実装は簡単ではないため、フレームワークによって <xref:System.Collections.ObjectModel.Collection%601> や <xref:System.Collections.ObjectModel.KeyedCollection%602> などのいくつかの基底クラスが提供されており、それらはカスタム コレクションを実装するためのヘルパーとして機能します。

 基底クラスは、含まれる実装が多すぎる傾向があるため、通常は、抽象化として使用するのに適していません。 たとえば、`Collection<T>` 基底クラスには、非ジェネリックの `IList` インターフェイスを実装するという事実 (非ジェネリックのコレクションとより適切に統合するため)、およびそれがメモリに格納されているそのフィールドの 1 つの項目のコレクションであるという事実に関連する、多くの実装が含まれています

 前に説明したように、基底クラスは、抽象化を実装する必要があるユーザーに貴重なヘルプを提供できますが、同時に大きな負担になる可能性もあります。 それらにより、表に出る部分が増え、継承階層が深くなるため、概念的にフレームワークの複雑さが増します。 したがって、基底クラスは、フレームワークのユーザーにとって大きな価値がある場合にのみ使用する必要があります。 フレームワークの実装担当者にのみ価値がある場合は、避ける必要があります。この場合は、基底クラスからの継承ではなく、内部実装へのデリゲートを検討することを強くお勧めします。

 ✔️ 抽象メンバーが含まれていない場合でも、基底クラスを抽象化することを検討します。 このようにすると、そのクラスが継承のためだけに設計されていることが、ユーザーに明確に伝わります。

 ✔️ 主要なシナリオの種類とは別の名前空間に、基底クラスを配置することを検討します。 定義上、基底クラスは高度な拡張シナリオのためのものなので、ほとんどのユーザーにとっては興味がありません。

 ❌ パブリック API での使用を意図されたクラスの場合は、基底クラスの名前に "Base" というサフィックスを付けないようにします。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [機能拡張のデザイン](designing-for-extensibility.md)
