---
description: '詳細情報: 型のデザインのガイドライン'
title: 型のデザインのガイドライン
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: d2c193d41dda118558cc5e7541f7e2dfbaf1a369
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641838"
---
# <a name="type-design-guidelines"></a>型のデザインのガイドライン

CLR の観点から見ると、型には参照型と値型という 2 つのカテゴリしかありませんが、フレームワークの設計について説明するために、ここでは、それぞれに固有の設計規則がある多数の論理グループに型を分割しています。

 クラスは、参照型の一般的なケースです。 それらは、大半のフレームワークで型の大部分を構成します。 クラスは、それらがサポートしているオブジェクト指向の充実した機能セットと一般的な適用性によって、広く使用されています。 基底クラスと抽象クラスは、拡張性に関連する特殊な論理グループです。

 インターフェイスは、参照型と値型の両方によって実装できる型です。 このため、参照型と値型の多様な形態の階層のルートとして機能できます。 さらに、インターフェイスを使用して、複数の継承をシミュレートできます。これは CLR ではネイティブにサポートされていません。

 構造体は値型の一般的なケースであり、言語プリミティブと同じように、小さく単純な型用に予約してください。

 列挙型は、値型の特殊なケースであり、曜日やコンソールの色などの短い値のセットを定義するために使用されます。

 静的クラスは、静的メンバーのためのコンテナー用の型です。 通常は、他の操作へのショートカットを提供するために使用されます。

 デリゲート、例外、属性、配列、およびコレクションは、すべてが特定の用途のための参照型の特殊なケースであり、その設計と使用に関するガイドラインについては、本書の別の場所で説明します。

 ✔️ 各型は、関連性のない機能のランダムなコレクションではなく、必ず関連するメンバーの適切に定義されたセットであるようにしてください。

## <a name="in-this-section"></a>このセクションの内容

 [クラスまたは構造体の選択](choosing-between-class-and-struct.md) [抽象クラスのデザイン](abstract-class.md) [静的クラスのデザイン](static-class.md) [インターフェイスのデザイン](interface.md) [構造体のデザイン](struct.md) [列挙型のデザイン](enum.md) [入れ子にされた型](nested-types.md) *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
