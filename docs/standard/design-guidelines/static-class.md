---
description: '詳細情報: 静的クラスのデザイン'
title: 静的クラスのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 16db470ab0975a5545617c9c5471d6ac157e688b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782469"
---
# <a name="static-class-design"></a>静的クラスのデザイン

静的クラスは、静的メンバーのみが含まれるクラスとして定義されます (もちろん、<xref:System.Object?displayProperty=nameWithType> から継承されるインスタンス メンバーと、プライベート コンストラクターがある場合はそれを除きます)。 一部の言語には、静的クラスのサポートが組み込まれています。 C# 2.0 以降では、クラスが静的として宣言されている場合、それはシールドで抽象であり、インスタンス メンバーをオーバーライドまたは宣言することはできません。

 静的クラスは、純粋なオブジェクト指向設計と単純さの間の妥協を表しています。 一般に、それらは、他の操作 (<xref:System.IO.File?displayProperty=nameWithType> など)、拡張メソッドのホルダー、または完全なオブジェクト指向ラッパーが保証されていない機能 (<xref:System.Environment?displayProperty=nameWithType> など) へのショートカットを提供するために使用されます。

 ✔️ 静的クラスは控えめに使用してください。

 静的クラスは、フレームワークのオブジェクト指向コアのサポート クラスとしてのみ使用する必要があります。

 ❌ 静的クラスを雑多なもののバケットとして扱わないでください。

 ❌ 静的クラスのインスタンス メンバーを宣言またはオーバーライドしないでください。

 ✔️ プログラミング言語に静的クラスの組み込みサポートがない場合は、静的クラスをシールドの抽象型として宣言し、プライベート インスタンス コンストラクターを追加します。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](type.md)
- [フレームワーク デザインのガイドライン](index.md)
