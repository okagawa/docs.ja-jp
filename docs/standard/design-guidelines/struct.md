---
description: '詳細情報: 構造体のデザイン'
title: 構造体のデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: a28dd3e452d22e61d95ec521fdbde6539e38ed78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641903"
---
# <a name="struct-design"></a>構造体のデザイン

汎用の値型は、ほとんどの場合、構造体と呼ばれます。これは C# のキーワードです。 このセクションでは、一般的な構造体の設計に関するガイドラインを示します。

 ❌ 構造体に対して、パラメーターのないコンストラクターを使用しないでください。

 このガイドラインに従うことで、配列の各項目にコンストラクターを実行することなく、構造体の配列を作成できます。 C# では、構造体でパラメーターのないコンストラクターは使用できないことに注意してください。

 ❌ 変更可能な値型を定義しないでください。

 変更可能な値型にはいくつかの問題があります。 たとえば、プロパティ ゲッターによって値型が返される場合、呼び出し元はコピーを受け取ります。 コピーは暗黙的に作成されるため、開発者は、元の値ではなくコピーを変更していることに気付かないことがあります。 また、一部の言語 (特に動的言語) では、ローカル変数であっても逆参照されるときにコピーが作成されるため、変更可能な値型の使用で問題が発生します。

 ✔️ すべてのインスタンス データが 0、false、または null (必要に応じて) に設定された状態が有効であるようにしてください。

 これにより、構造体の配列が作成されるときに、無効なインスタンスが誤って作成されることが防止されます。

 ✔️ 値型に <xref:System.IEquatable%601> を実装してください。

 値型の <xref:System.Object.Equals%2A?displayProperty=nameWithType> メソッドによってボックス化が発生しますが、リフレクションが使用されるため、既定の実装はあまり効率的ではありません。 <xref:System.IEquatable%601.Equals%2A> のほうがパフォーマンスがはるかに優れており、ボックス化が発生しないように実装できます。

 ❌ <xref:System.ValueType> を明示的に拡張しないでください。 実際、ほとんどの言語ではこれは禁止されています。

 一般に、構造体は非常に有用ですが、頻繁にボックス化されない小さな単一の変更できない値に対してのみ使用するようにしてください。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](type.md)
- [フレームワーク デザインのガイドライン](index.md)
- [クラスまたは構造体の選択](choosing-between-class-and-struct.md)
