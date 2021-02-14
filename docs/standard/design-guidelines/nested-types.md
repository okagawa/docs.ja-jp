---
description: '詳細情報: 入れ子にされた型'
title: 入れ子にされた型
ms.date: 10/22/2008
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: 07d81827d67e50351f442ec15ca6cb18a63160fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713378"
---
# <a name="nested-types"></a>入れ子にされた型

入れ子にされた型は、外側の型と呼ばれる別の型のスコープ内で定義された型です。 入れ子にされた型は、それを囲む型のすべてのメンバーにアクセスできます。 たとえば、外側の型で定義されているプライベート フィールドや、囲む型のすべての先祖で定義されている保護されたフィールドにアクセスできます。

 一般に、入れ子にされた型は控えめに使用する必要があります。 直接呼び出すべきではないいくつかの理由があります。 一部の開発者は、この概念について完全には理解していません。 たとえば、そのような開発者は、入れ子にされた型の変数を宣言する構文で問題が発生する可能性があります。 入れ子にされた型はそれを囲む型と密接に結び付けられているため、汎用的な型には適していません。

 入れ子にされた型は、それを囲む型の実装の詳細をモデル化する場合に最適です。 エンド ユーザーは、入れ子にされた型の変数を宣言する必要はあまりなく、入れ子にされた型を明示的にインスタンス化する必要はほとんどありません。 たとえば、コレクションの列挙子は、そのコレクションの入れ子にされた型にすることができます。 通常、列挙子はそれを囲む型によってインスタンス化され、多くの言語では foreach ステートメントがサポートされているため、エンド ユーザーが列挙子変数を宣言する必要はほとんどありません。

 ✔️ 入れ子にされた型とその外側の型の関係が、メンバーのアクセシビリティ セマンティクスが望ましいものである場合は、入れ子にされた型を使用ます。

 ❌ 入れ子にされたパブリック型を論理グループ化構成体として使用しないでください。この場合は名前空間を使用します。

 ❌ 入れ子にされた型をパブリックに公開しないでください。 唯一の例外は、サブクラス化のようなまれなシナリオや、その他の高度なカスタマイズ シナリオで、入れ子にされた型の変数を宣言する必要がある場合だけです。

 ❌ 含んでいる型の外側で型が参照される可能性が高い場合は、入れ子にされた型を使用しないでください。

 たとえば、クラスで定義されたメソッドに渡される列挙型を、入れ子にされた型としてクラスで定義することはできません。

 ❌ クライアントのコードでインスタンス化する必要がある場合は、入れ子にされた型を使用しないでください。  型にパブリック コンストラクターがある場合は、入れ子にしてはならない可能性があります。

 型をインスタンス化できる場合、フレームワーク内にその型独自の場所があることを示している可能性があり (外側の型を使用しないで作成、操作、破棄できます)、入れ子にすることはできません。 外側の型への何らかの関係なしに、外側の型の外部で内側の型を広く再利用することはできません。

 ❌ インターフェイスのメンバーとして、入れ子にされた型を定義しないでください。 多くの言語では、そのようなコンストラクトはサポートされていません。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](type.md)
- [フレームワーク デザインのガイドライン](index.md)
