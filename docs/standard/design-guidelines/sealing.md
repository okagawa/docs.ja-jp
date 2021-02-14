---
description: '詳細情報: シール'
title: シール
ms.date: 10/22/2008
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: 94673f793aa7373e1076e13cbda900fba83786f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731722"
---
# <a name="sealing"></a>シール

オブジェクト指向フレームワークの機能の 1 つは、フレームワーク デザイナーが予期しないような方法で、開発者がそれを拡張およびカスタマイズできることです。 これは、拡張可能な設計の威力であると同時に危険性でもあります。 したがって、フレームワークを設計するときは、拡張性が望ましいときはそれを慎重に設計し、危険なときは拡張性を制限することが非常に重要です。

 拡張性を防ぐための強力なメカニズムがシールです。 クラスまたは個々のメンバーをシールできます。 クラスをシールすると、ユーザーはそのクラスから継承できなくなります。 メンバーをシールすると、ユーザーは特定のメンバーをオーバーライドできなくなります。

 ❌ それを行う十分な理由なしに、クラスをシールしないでください。

 拡張シナリオを思い付かないためにクラスをシールすることは、適切な理由ではありません。 フレームワークのユーザーは、便利なメンバーの追加のような、よくわからないさまざまな理由でクラスを継承することを好みます。 ユーザーが型を継承しようとする明白でない理由の例については、「[シールされていないクラス](unsealed-classes.md)」を参照してください。

 クラスをシールする適切な理由としては、次のようなものがあります。

- クラスが静的クラスである。 「[静的クラスのデザイン](static-class.md)」を参照してください。

- クラスの継承されたプロテクト メンバーに、セキュリティ上の注意が必要なシークレットが格納される。

- クラスで多くの仮想メンバーが継承されており、それらを個別にシールするコストが、クラスをアンシールドのままにする利点よりも大きい。

- クラスが、非常に高速のランタイム参照を必要とする属性である。 シールド属性の方が、アンシールドのものより、パフォーマンス レベルが若干高くなります。 「[属性](attributes.md)」を参照してください。

 ❌ シールド型では、プロテクト メンバーまたは仮想メンバーを宣言しないでください。

 定義により、シールド型から継承することはできません。 つまり、シールド型のプロテクト メンバーを呼び出すことはできず、シールド型の仮想メソッドをオーバーライドすることはできません。

 ✔️ オーバーライドするメンバーをシールすることを検討します。

 仮想メンバーの導入によって発生する可能性のある問題 (「[仮想メンバー](virtual-members.md)」で説明されています) は、程度は若干低くなりますが、オーバーライドにも当てはまります。 オーバーライドをシールすると、継承階層内のそのポイント以降について、これらの問題を防ぐことができます。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [機能拡張のデザイン](designing-for-extensibility.md)
- [シールされていないクラス](unsealed-classes.md)
