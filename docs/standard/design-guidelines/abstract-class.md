---
description: '詳細情報: 抽象クラスのデザイン'
title: 抽象クラスのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 5b1cd833bf43e5bf5731176243809393187e84d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642462"
---
# <a name="abstract-class-design"></a>抽象クラスのデザイン

❌ 抽象型では、パブリックの、または保護された内部コンストラクターを定義しないでください。

 ユーザーがその型のインスタンスを作成する必要がある場合にのみ、コンストラクターをパブリックにする必要があります。 抽象型のインスタンスは作成できないため、パブリック コンストラクターのある抽象型は不適切な設計になり、ユーザーの誤解を招きます。

 ✔️ 抽象クラスでは、保護されたコンストラクターまたは内部コンストラクターを定義します。

 保護されたコンストラクターの方が一般的であり、サブタイプの作成時に基底クラスによる独自の初期化の実行を許可するだけです。

 内部コンストラクターを使用すると、抽象クラスの具象実装を、クラスを定義するアセンブリに制限できます。

 ✔️ 出荷する各抽象クラスから継承される具象型を少なくとも 1 つ提供します。

 これにより、抽象クラスの設計を検証できます。 たとえば、<xref:System.IO.FileStream?displayProperty=nameWithType> は <xref:System.IO.Stream?displayProperty=nameWithType> 抽象クラスの実装です。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](type.md)
- [フレームワーク デザインのガイドライン](index.md)
