---
description: '詳細情報: 例外とパフォーマンス'
title: 例外とパフォーマンス
ms.date: 10/22/2008
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: 72b35ccca5514e56dcc04fc0a07d1f9887c4a2f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642124"
---
# <a name="exceptions-and-performance"></a>例外とパフォーマンス

例外に関する一般的な懸念の 1 つとして、日常的に失敗するコードに例外を使用すると、実装のパフォーマンスが許容できないものになるだろうということがあります。 これはもっともな心配です。 メンバーによって例外がスローされる場合、そのパフォーマンスが桁違いに低下する可能性があります。 ただし、エラー コードの使用を禁止する例外ガイドラインに厳密に準拠しながら、優れたパフォーマンスを達成することができます。 このセクションで説明する 2 つのパターンは、これを行う方法を提案しています。

 ❌ 例外によるパフォーマンスへの悪影響の可能性が心配であるという理由で、エラー コードを使用しないでください。

 パフォーマンスを向上させるために、次の 2 つのセクションで説明する、Tester-Doer パターンまたは Try-Parse パターンを使用できます。

## <a name="tester-doer-pattern"></a>Tester-Doer パターン

 例外をスローするメンバーを 2 つに分割することで、メンバーのパフォーマンスを向上させることができる可能性があります。 <xref:System.Collections.Generic.ICollection%601> インターフェイスの <xref:System.Collections.Generic.ICollection%601.Add%2A> メソッドを見てみましょう。

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 コレクションが読み取り専用の場合、メソッド `Add` によって (例外が) スローされます。 これは、このメソッドの呼び出しが頻繁に失敗することが予想されるシナリオでは、パフォーマンスの問題になる可能性があります。 この問題を軽減する方法の 1 つは、値を追加する前に、コレクションが書き込み可能かどうかをテストすることです。

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 条件をテストするために使用されるメンバー (この例では `IsReadOnly` プロパティ) を Tester と呼びます。 可能性があるスロー操作を実行するために使用されるメンバー (この例では `Add` メソッド) を Doer と呼びます。

 ✔️ 例外に関連するパフォーマンスの問題を回避するために、一般的なシナリオで例外をスローする可能性のあるメンバーに対して Tester-Doer パターンを使用することを検討してください。

## <a name="try-parse-pattern"></a>Try-Parse パターン

 パフォーマンスが非常に重要な API では、前のセクションで説明した Tester-Doer パターンよりも高速なパターンを使用する必要があります。 このパターンでは、メンバー名を調整して、適切に定義されたテスト ケースをメンバー セマンティクスの一部にするための呼び出しが行われます。 たとえば、<xref:System.DateTime> では、文字列の解析が失敗した場合に例外をスローする <xref:System.DateTime.Parse%2A> メソッドが定義されます。 解析を試行する対応する <xref:System.DateTime.TryParse%2A> メソッドも定義されますが、解析が失敗した場合は false が返され、解析が成功した場合はその結果が `out` パラメーターを使用して返されます。

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 このパターンを使用する場合は、Try 機能を厳しい条件で定義することが重要です。 明確に定義された Try 以外の理由でメンバーが失敗した場合でも、メンバーによって対応する例外がスローされる必要があります。

 ✔️ 例外に関連するパフォーマンスの問題を回避するには、一般的なシナリオで例外をスローする可能性のあるメンバーに対して Try-Parse パターンを使用することを検討してください。

 ✔️ このパターンを実装するメソッドには、"Try" というプレフィックスとブール型の戻り値を使用してください。

 ✔️ Try-Parse パターンを使用して、メンバーごとに例外をスローするメンバーを用意してください。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [例外のデザインのガイドライン](exceptions.md)
