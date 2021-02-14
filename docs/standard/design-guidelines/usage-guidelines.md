---
description: '詳細情報: 使用ガイドライン'
title: 使用上のガイドライン
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: a435fab2adb00f671dfde1619a3c1f8db719d9df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641799"
---
# <a name="usage-guidelines"></a>使用上のガイドライン

このセクションには、パブリックにアクセスできる API で共通型を使用するためのガイドラインが含まれています。 組み込みのフレームワーク型 (シリアル化属性など) の直接使用と、一般的な演算子のオーバーロードを扱っています。
  
<xref:System.IDisposable?displayProperty=nameWithType> インターフェイスはこのセクションでは説明されていません。[Dispose パターン](../garbage-collection/implementing-dispose.md) セクションで説明されています。

> [!NOTE]
> その他の共通する組み込みの .NET Framework の型のガイドラインとその他の情報については、次に関するリファレンス トピックを参照してください。<xref:System.DateTime?displayProperty=nameWithType>、<xref:System.DateTimeOffset?displayProperty=nameWithType>、<xref:System.ICloneable?displayProperty=nameWithType>、<xref:System.IComparable%601?displayProperty=nameWithType>、<xref:System.IEquatable%601?displayProperty=nameWithType>、<xref:System.Nullable%601?displayProperty=nameWithType>、<xref:System.Object?displayProperty=nameWithType>、<xref:System.Uri?displayProperty=nameWithType>。

## <a name="in-this-section"></a>このセクションの内容

[配列](arrays.md)  
[属性](attributes.md)  
[コレクション](guidelines-for-collections.md)  
[シリアル化](serialization.md)  
[System.Xml の使用法](system-xml-usage.md)  
[等値演算子](equality-operators.md)  

*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
