---
description: '詳細情報: フィールドのデザイン'
title: フィールドのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 88df60c3050035221dc65429bbd543c71d5d69b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642046"
---
# <a name="field-design"></a>フィールドのデザイン

カプセル化の原則は、オブジェクト指向設計で最も重要な概念の 1 つです。 この原則では、オブジェクト内に格納されるデータは、そのオブジェクトに対してのみアクセスできるようにする必要であると述べられています。

 この原則を解釈するのに役立つ方法は、型のメンバー以外のコードを中断することなく、型のフィールドに対する変更 (名前または型の変更) を実行できるように型を設計する必要があると言うことです。 この解釈は、すべてのフィールドをプライベートにする必要があることを意味します。

 本書では、この厳格な制限から定数と静的読み取り専用フィールドを除外しています。理由は、そのようなフィールドは、その定義からいって、変更する必要がないからです。

 ❌ パブリックまたは保護されているインスタンス フィールドを用意しないでください。

 フィールドをパブリックまたは保護するのではなく、フィールドにアクセスするためのプロパティを指定してください。

 ✔️ 変更されることがない定数には定数フィールドを使用してください。

 コンパイラでは、定数フィールドの値が呼び出し側コードに直接書き込まれます。 そのため、定数値は、互換性を損なうリスクなしで変更することはできません。

 ✔️ 定義済みのオブジェクト インスタンスには、パブリックで静的な `readonly` フィールドを使用してください。

 型の定義済みインスタンスがある場合は、型自体のパブリックな読み取り専用の静的フィールドとして宣言してください。

 ❌ `readonly` フィールドに変更可能な型のインスタンスを割り当てないでください。

 変更可能な型は、インスタンス化された後で変更できるインスタンスを持つ型です。 たとえば、配列、ほとんどのコレクション、およびストリームは変更可能な型ですが、<xref:System.Int32?displayProperty=nameWithType>、<xref:System.Uri?displayProperty=nameWithType>、および <xref:System.String?displayProperty=nameWithType> はすべて不変です。 参照型フィールドの読み取り専用修飾子によって、フィールドに格納されているインスタンスの置換が防止されますが、インスタンスを変更する呼び出し元のメンバーによるフィールドのインスタンス データの変更は防止されません。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](member.md)
- [フレームワーク デザインのガイドライン](index.md)
