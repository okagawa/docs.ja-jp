---
description: override 修飾子 - C# リファレンス
title: override 修飾子 - C# リファレンス
ms.date: 10/22/2020
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 618200183348e68a4600adb9592a635f61f6a875
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434879"
---
# <a name="override-c-reference"></a>override (C# リファレンス)

`override` 修飾子は、継承したメソッド、プロパティ、インデクサー、またはイベントの抽象実装または仮想実装を拡張したり修飾したりする際に必要です。

次の例では、`Square` クラスが `GetArea` のオーバーライドされる実装を提供する必要があります。これは、`GetArea` が `Shape` 抽象クラスから継承されているためです。

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

`override` メソッドは、基底クラスから継承されるメソッドの新しい実装を提供します。 `override` 宣言によってオーバーライドされるメソッドを、オーバーライドされる基本メソッドと言います。 `override` メソッドには、オーバーライドされる基本メソッドと同じシグネチャが必要です。 C# 9.0 以降、共変の戻り値の型が `override` メソッドによってサポートされています。 特に、`override` メソッドの戻り値の型は、対応する基本メソッドの戻り値の型から派生できます。 C# 8.0 以前の場合、`override` メソッドとオーバーライドされた基本メソッドの戻り値の型は同じである必要があります。

非仮想メソッドまたは静的メソッドをオーバーライドすることはできません。 オーバーライドされる基本メソッドは、`virtual`、`abstract`、`override` のいずれかである必要があります。

`override` 宣言は、`virtual` メソッドのアクセシビリティを変更できません。 `override` メソッドと `virtual` メソッドの両方に、同じ[アクセス レベル修飾子](access-modifiers.md)が必要です。

`override` メソッドの修飾に、修飾子 `new`、`static`、または `virtual` は使用できません。

オーバーライドするプロパティの宣言では、継承されるプロパティとまったく同じアクセス修飾子、型、および名前を指定する必要があります。 C# 9.0 以降、共変の戻り値の型が読み取り専用のオーバーライドするプロパティによってサポートされています。 オーバーライドされたプロパティは、`virtual`、`abstract`、または `override` である必要があります。

`override` キーワードの使い方の詳細については、「[Override キーワードと New キーワードによるバージョン管理](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」を参照してください。 継承については、「[継承](../../programming-guide/classes-and-structs/inheritance.md)」を参照してください。

## <a name="example"></a>例

この例では、`Employee` という基底クラスと、`SalesEmployee` という派生クラスを定義します。 `SalesEmployee` クラスには追加のフィールド `salesbonus` があり、このフィールドを処理に含めるために、`CalculatePay` メソッドをオーバーライドします。

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)に関するページの「[オーバーライド メソッド](~/_csharplang/spec/classes.md#override-methods)」セクションを参照してください。

共変の戻り値の型の詳細については、[機能提案メモ](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)を参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [継承](../../programming-guide/classes-and-structs/inheritance.md)
- [C# キーワード](index.md)
- [修飾子](index.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [new (修飾子)](new-modifier.md)
- [ポリモーフィズム](../../programming-guide/classes-and-structs/polymorphism.md)
