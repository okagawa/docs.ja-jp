---
title: 抽象化の実装用の基本クラス
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: 6af63373b7cbb571265f14ac36028953525fcc7f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280570"
---
# <a name="base-classes-for-implementing-abstractions"></a>抽象化の実装用の基本クラス
厳密に言えば、クラスは、別のクラスが派生しているときに基底クラスになります。 ただし、このセクションでは、基底クラスは、主に共通の抽象化を提供するか、継承を使用して他のクラスが既定の実装を再利用することを目的として設計されたクラスです。 基本クラスは、通常、階層のルートにある抽象化と下部に複数のカスタム実装の間で、継承階層の中間に配置されます。

 抽象化を実装するための実装ヘルパーとして機能します。 たとえば、順序付けられた項目のコレクションに対するフレームワークの抽象化の1つは、 <xref:System.Collections.Generic.IList%601> インターフェイスです。 を実装する <xref:System.Collections.Generic.IList%601> ことは簡単ではないため、フレームワークには、 <xref:System.Collections.ObjectModel.Collection%601> <xref:System.Collections.ObjectModel.KeyedCollection%602> カスタムコレクションを実装するためのヘルパーとして機能するやなどのいくつかの基本クラスが用意されています。

 基底クラスは、実装が過剰になる傾向があるため、通常は抽象化として使用するのに適していません。 たとえば、基底クラスには、非ジェネリック `Collection<T>` インターフェイスを実装するという事実に関連する多くの実装が含まれてい `IList` ます (非ジェネリックコレクションとの互換性を高めるため)。また、そのフィールドの1つでメモリに格納されている項目のコレクションであるという事実にも対応しています。

 既に説明したように、基本クラスでは、抽象化を実装する必要があるユーザーにとって貴重なヘルプを提供できますが、同時に重要な責任を負うこともできます。 これらのユーザーは、領域を追加し、継承階層の深さを増やして、概念的にフレームワークを複雑にします。 したがって、基本クラスは、フレームワークのユーザーに大きな価値を提供する場合にのみ使用してください。 フレームワークの実装に対してのみ値を提供する場合は避ける必要があります。この場合、基本クラスからの継承ではなく、内部実装への委任を厳密に考慮する必要があります。

 抽象メンバーが含まれていない場合でも、基底クラスを抽象化することを検討✔️。 これにより、クラスを継承するためだけに設計されているユーザーに明確に通信できます。

 ✔️、主要なシナリオの種類とは別の名前空間に基本クラスを配置することを検討してください。 定義上、基本クラスは高度な拡張シナリオを対象としているため、ほとんどのユーザーにとっては興味がありません。

 ❌クラスがパブリック Api での使用を目的としている場合は、基底クラスに "Base" サフィックスを付けるのは避けてください。

 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワークデザインのガイドライン](index.md)
- [機能拡張のデザイン](designing-for-extensibility.md)
