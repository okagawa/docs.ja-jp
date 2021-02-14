---
description: '詳細情報: 演算子のオーバーロード'
title: 演算子のオーバーロード
ms.date: 10/22/2008
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: e6552f35081afa542e4dc14239206a63c7c1bd59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713326"
---
# <a name="operator-overloads"></a>演算子のオーバーロード

演算子のオーバーロードを使用すると、フレームワークの型を組み込みの言語プリミティブのように使用することができます。

 状況によっては許可され、役に立つこともありますが、演算子のオーバーロードは慎重に使用する必要があります。 フレームワーク デザイナーが簡単なメソッドにする必要がある操作に対して演算子を使い始めた場合など、演算子のオーバーロードの使用方法が正しくない多くのケースがあります。 以下のガイドラインは、演算子のオーバーロードを使用するタイミングと方法を決定するのに役立ちます。

 ❌ プリミティブ (組み込み) 型のように感じられるようにする必要がある型以外には、演算子のオーバーロードを定義しないでください。

 ✔️ プリミティブ型のように感じられるようにする必要がある型には、演算子のオーバーロードを定義することを検討します。

 たとえば、<xref:System.String?displayProperty=nameWithType> には `operator==` と `operator!=` が定義されています。

 ✔️ 数値を表す構造体で演算子のオーバーロードを定義します (<xref:System.Decimal?displayProperty=nameWithType> など)。

 ❌ 凝った演算子のオーバーロードを定義しないでください。

 演算子のオーバーロードは、演算の結果がすぐにわかる場合に便利です。 たとえば、ある <xref:System.DateTime> を別の `DateTime` から減算して <xref:System.TimeSpan> を取得できるようにするのは理にかなっています。 一方、2 つのデータベース クエリの和集合を求めるために論理和演算子を使用をしたり、ストリームに書き込むためにシフト演算子を使用したりするのは適切ではありません。

 ❌ 少なくとも 1 つのオペランドがオーバーロードを定義する型でない限り、演算子のオーバーロードを指定しないでください。

 ✔️ 演算子のオーバーロードは対称的になるようにします。

 たとえば、`operator==` をオーバーロードする場合は、`operator!=` もオーバーロードする必要があります。 同様に、`operator<` をオーバーロードする場合は、`operator>` もオーバーロードする必要があります。

 ✔️ メソッドには、オーバーロードされる各演算子に対応するフレンドリ名を付けることを検討します。

 多くの言語では、演算子のオーバーロードはサポートされていません。 このため、オーバーロード演算子には、同等の機能を提供するドメイン固有の適切な名前を持つ二次的なメソッドを含めることをお勧めします。

 次の表では、演算子とそれに対応するわかりやすいメソッド名の一覧を示します。

|C# の演算子シンボル|メタデータ名|フレンドリ名|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a>operator == のオーバーロード

 `operator ==` のオーバーロードは非常に複雑です。 演算子のセマンティクスは、<xref:System.Object.Equals%2A?displayProperty=nameWithType> など、他のいくつかのメンバーと互換性がある必要があります。

### <a name="conversion-operators"></a>変換演算子

 変換演算子は、ある型から別の型に変換できる単項演算子です。 演算子は、オペランドまたは戻り値の型のいずれかで静的メンバーとして定義されている必要があります。 変換演算子には、暗黙と明示の 2 種類があります。

 ❌ エンド ユーザーがそのような変換を明確に想定していない場合は、変換演算子を提供しないでください。

 ❌ 型のドメインの外部で変換演算子を定義しないでください。

 たとえば、<xref:System.Int32>、<xref:System.Double>、<xref:System.Decimal> はすべて数値型ですが、<xref:System.DateTime> はそうではありません。 したがって、`Double(long)` を `DateTime` に変換する変換演算子は定義しないようにする必要があります。 このような場合は、コンストラクターを使用することをお勧めします。

 ❌ 変換で損失が発生する可能性がある場合は、暗黙的な変換演算子を提供しないでください。

 たとえば、`Double` の方が `Int32` より範囲が広いので、`Double` から `Int32` への暗黙的な変換を行うことはできません。 変換で損失が発生する可能性がある場合でも、明示的な変換演算子は提供できます。

 ❌ 暗黙のキャストから例外をスローしないでください。

 変換が行われていることがわからない可能性があるため、エンド ユーザーにとって起きていることを理解するのは非常に困難です。

 ✔️ キャスト演算子の呼び出しによって損失を伴う変換が発生し、演算子のコントラクトでは損失を伴う変換が許可されていない場合は、<xref:System.InvalidCastException?displayProperty=nameWithType> をスローします。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](member.md)
- [フレームワーク デザインのガイドライン](index.md)
