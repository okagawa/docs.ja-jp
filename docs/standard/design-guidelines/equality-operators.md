---
description: '詳細情報: 等値演算子'
title: 等値演算子
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 8678ed1b4bc320f685cf7ae172f064b3dededd04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642241"
---
# <a name="equality-operators"></a>等値演算子

このセクションでは、等値演算子のオーバーロードについて説明し、`operator==` と `operator!=` を等値演算子と呼びます。

 ❌ 等値演算子のどちらか一方だけをオーバーロードしないでください。

 ✔️ <xref:System.Object.Equals%2A?displayProperty=nameWithType> と等値演算子が、まったく同じセマンティクスを持ち、同じようなパフォーマンス特性を備えるようにします。

 これは、多くの場合、等値演算子をオーバーロードするときは、`Object.Equals` をオーバーライドする必要があることを意味します。

 ❌ 等値演算子からは例外をスローしないでください。

 たとえば、いずれかの引数が null の場合は、`NullReferenceException` をスローするのではなく、false を返します。

## <a name="equality-operators-on-value-types"></a>値型での等値演算子

 ✔️ 等値性に意味がある場合は、値型で等値演算子をオーバーロードます。

 ほとんどのプログラミング言語では、値型に `operator==` の既定の実装はありません。

## <a name="equality-operators-on-reference-types"></a>参照型での等値演算子

 ❌ 変更可能な参照型では、等値演算子をオーバーロードしないでください。

 多くの言語には、参照型に組み込みの等値演算子があります。 通常、組み込みの演算子には参照の等値性が実装されており、多くの開発者は、既定の動作が値の等値性に変更されると驚きます。

 不変性によって参照の等値性と値の等値性の違いがわかりにくくなるため、この問題は、変更不可能な参照型については軽減されます。

 ❌ 実装が参照の等値性のものより大幅に遅くなる場合は、参照型で等値演算子をオーバーロードしないでください。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [使用方法のガイドライン](usage-guidelines.md)
