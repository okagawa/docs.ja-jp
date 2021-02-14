---
description: '詳細情報: 属性'
title: 属性
ms.date: 10/22/2008
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 1557ba0945da0c8498c67f70ba4a01dd0bbe432e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642423"
---
# <a name="attributes"></a>属性

<xref:System.Attribute?displayProperty=nameWithType> は、カスタム属性を定義するために使用される基底クラスです。

 属性は、アセンブリ、型、メンバー、パラメーターなどのプログラミング要素に追加できる注釈です。 それらは、アセンブリのメタデータに格納され、リフレクション API を使用して実行時にアクセスできます。 たとえば、フレームワークによって定義されている <xref:System.ObsoleteAttribute> を型またはメンバーに適用して、その型またはメンバーが非推奨になったことを示すことができます。

 属性には、属性に関連する追加データを保持する 1 つ以上のプロパティを設定できます。 たとえば、`ObsoleteAttribute` は、型またはメンバーが非推奨になったリリース、および古い API を置き換える新しい API の説明に関する追加情報を保持できます。

 属性の一部のプロパティは、属性を適用するときに指定する必要があります。 これらは、位置指定のコンストラクター パラメーターとして表されるため、必須プロパティまたは必須引数と呼ばれます。 たとえば、<xref:System.Diagnostics.ConditionalAttribute> の <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> プロパティは必須プロパティです。

 属性が適用されるときに必ずしも指定する必要がないプロパティは、省略可能なプロパティ (または省略可能な引数) と呼ばれます。 それらは、設定可能なプロパティによって表されます。 コンパイラには、属性が適用されるときにこれらのプロパティを設定するための特別な構文が用意されています。 たとえば、<xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> プロパティは省略可能な引数を表します。

 ✔️ カスタム属性クラスの名前には "Attribute" というサフィックスを付けます。

 ✔️ カスタム属性には <xref:System.AttributeUsageAttribute> を適用します。

 ✔️ 省略可能な引数には設定可能なプロパティを提供します。

 ✔️ 必須の引数には取得専用のプロパティを提供します。

 ✔️ 必須の引数に対応するプロパティを初期化するためのコンストラクター パラメーターを提供ます。 各パラメーターの名前は、対応するプロパティと同じにする必要があります (ただし、異なる大文字と小文字の使い分けで)。

 ❌ 省略可能な引数に対応するプロパティを初期化するためのコンストラクター パラメーターは提供しないようにします。

 つまり、コンストラクターとセッターの両方で設定できるプロパティがないようにします。 このガイドラインにより、省略可能な引数と必須の引数の区別が非常に明確になり、同じことを 2 つの方法で行うことが回避されます。

 ❌ カスタム属性コンストラクターをオーバーロードしないようにします。

 コンストラクターを 1 つだけにすると、どの引数が必須で、どれが省略可能であるかが、ユーザーに明確に伝わります。

 ✔️ 可能であれば、カスタム属性クラスをシールします。 これにより、属性の参照が高速になります。

 *Portions &copy; 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [使用方法のガイドライン](usage-guidelines.md)
