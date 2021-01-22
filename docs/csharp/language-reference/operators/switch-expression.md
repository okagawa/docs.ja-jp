---
title: switch 式 - C# リファレンス
description: パターン マッチングとその他のデータ イントロスペクションに C# の switch 式を使用する方法について説明します
ms.date: 01/14/2021
ms.openlocfilehash: 55fef8d351b178fd0ec23847e81e6c56eb1367b0
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536087"
---
# <a name="switch-expression-c-reference"></a>switch 式 (C# リファレンス)

この記事では、C# 8.0 で導入された `switch` 式について説明します。 `switch` ステートメントについては、[ステートメント](../keywords/index.md)のセクションの [`switch` ステートメント](../keywords/switch.md)に関する記事を参照してください。

## <a name="basic-example"></a>基本的な例

`switch` 式では、式のコンテキストにおいて `switch` と同様のセマンティクスが提供されます。 switch アームで値が生成されるときの簡潔な構文が提供されます。 次の例では、switch 式の構造を示します。 オンライン マップでの視方向を表す `enum` の値が、対応する基本方位に変換されます。

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetBasicStructure":::

前のサンプルでは、switch 式の基本的な要素が示されています。

- "*範囲式*": 前の例では、変数 `direction` が範囲式として使用されています。
- "*switch 式アーム*": 各 switch 式アームには、"*パターン*"、省略可能な "*ケース ガード*"、`=>` トークン、"*式*" が含まれています。

"*switch 式の結果*" は、"*パターン*" が "*範囲式*" と一致し、"*ケース ガード*" が `true` と評価される (存在する場合)、最初の "*switch 式アーム*" の式の値です。 `=>` トークンの右側の "*式*" として、式ステートメントを使用することはできません。

"*switch 式アーム*" は、テキストの順番に評価されます。 高い "*switch 式アーム*" がすべての値と一致するため、低い "*switch 式アーム*" を選択できない場合、コンパイラではエラーが発行されます。

## <a name="patterns-and-case-guards"></a>パターンとケース ガード

switch 式アームでは、多くのパターンがサポートされています。 前の例では "*定数パターン*" が使用されています。 "*定数パターン*" では、範囲式と値が比較されます。 その値は、コンパイル時定数である必要があります。 "*型パターン*" では、範囲式と既知の型が比較されます。 次の例では、シーケンスから 3 番目の要素が取得されます。 シーケンスの型に基づいて、異なるメソッドが使用されます。

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetTypePattern":::

パターンは再帰的にすることができます。パターンで型をテストし、その型が一致する場合、そのパターンは範囲式の 1 つまたは複数のプロパティ値と一致します。 再帰パターンを使用して、前の例を拡張できます。 要素数が 3 未満の配列に対する switch 式アームを追加します。 再帰パターンを次の例に示します。

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetRecursivePattern":::

再帰パターンでは、範囲式のプロパティを調べることはできますが、任意のコードを実行することはできません。 `when` 句で指定する "*ケース ガード*" を使用して、他のシーケンス型と同様のチェックを行うことができます。

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetGuardCase":::

最後に、`_` パターンと `null` パターンを追加して、他のどの switch 式アームによっても処理されない引数をキャッチすることができます。 そのようにすると、switch 式が "*網羅的*" になります。これは、範囲式で可能性のあるすべての値が処理されることを意味します。 次の例では、そのような式アームを追加しています。

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetExhaustive":::

前の例では、`null` パターンが追加され、`IEnumerable<T>` 型パターンが `_` パターンに変更されています。 `null` パターンでは、switch 式アームとして null チェックが提供されます。 そのアームの式によって、<xref:System.ArgumentNullException> がスローされます。 `_` パターンは、それより前にあるアームで一致していないすべての入力と一致します。 `null` チェックの後で指定する必要があります。そうしないと、`null` 入力と一致します。

## <a name="non-exhaustive-switch-expressions"></a>網羅的でない switch 式

switch 式のどのパターンでも引数がキャッチされない場合、ランタイムで例外がスローされます。 .NET Core 3.0 以降のバージョンでは、例外は <xref:System.Runtime.CompilerServices.SwitchExpressionException?displayProperty=nameWithType> です。 .NET Framework では、例外は <xref:System.InvalidOperationException> です。

## <a name="see-also"></a>関連項目

- [再帰パターンに関する C# 言語仕様の提案](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)
- [C# リファレンス](../index.md)
- [C# の演算子と式](index.md)
- [パターン マッチング](../../pattern-matching.md)
