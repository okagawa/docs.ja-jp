---
description: '詳細情報: 配列'
title: 配列
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 2d919d5e13a03ed1c5d090339f8f0fd9c1a79190
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642448"
---
# <a name="arrays"></a>配列

✔️ パブリック API では、配列よりコレクションを使用するようにします。 コレクションと配列の選択方法の詳細については、「[コレクション](guidelines-for-collections.md)」セクションを参照してください。

 ❌ 読み取り専用の配列フィールドは使用しないでください。 フィールド自体は読み取り専用であり、変更できませんが、配列内の要素は変更できます。

 ✔️ 多次元配列ではなくジャグ配列を使用することを検討します。

 ジャグ配列は、その要素も配列である配列です。 要素を構成する配列のサイズは異なってもよいため、データ セットによっては (スパース マトリックスなど)、多次元配列より無駄な空間が少なくなります。 さらに、ジャグ配列では CLR によってインデックス操作が最適化されるため、一部のシナリオで実行時のパフォーマンスが向上する可能性があります。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- <xref:System.Array>
- [フレームワーク デザインのガイドライン](index.md)
- [使用方法のガイドライン](usage-guidelines.md)
