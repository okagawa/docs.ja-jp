---
title: 文字列を部分文字列に分離する
description: String.Split、正規表現、String.Substring など、文字列の一部を抽出するさまざまな手法について説明します。
ms.date: 10/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], breaking up
ms.openlocfilehash: b753476b7d8e5808fdcacc6f28bd1de5f8b232bb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829650"
---
# <a name="extract-substrings-from-a-string"></a>文字列から部分文字列を抽出する

この記事では、文字列の一部を抽出するためのさまざまな手法について説明します。

- 目的の部分文字列が既知の区切り文字 (1 つまたは複数) で区切られている場合は、[Split メソッド](#stringsplit-method)を使用します。
- 文字列が固定パターンに準拠している場合は、[正規表現](#regular-expressions)が便利です。
- 文字列内の "*すべての*" 部分文字列を抽出したくないときは、[IndexOf メソッドと Substring メソッド](#stringindexof-and-stringsubstring-methods)を組み合わせて使用します。

## <a name="stringsplit-method"></a>String.Split メソッド

<xref:System.String.Split%2A?displayProperty=nameWithType> には、指定した 1 つ以上の区切り文字に基づいて文字列を部分文字列のグループに分割するのに役立つ、いくつかのオーバーロードが用意されています。 最終結果の部分文字列の合計数を制限したり、部分文字列から空白文字を取り除いたり、空の部分文字列を除外したりできます。

次の例では、`String.Split()` の 3 つの異なるオーバーロードを示します。 最初の例では、区切り文字を渡さずに <xref:System.String.Split(System.Char[])> のオーバーロードを呼び出します。 区切り文字を指定しないと、`String.Split()` により、文字列を分割するための既定の区切り記号 (空白文字) が使用されます。

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#1)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="1":::

ご覧のように、部分文字列の 2 つにピリオド文字 (`.`) が含まれています。 ピリオド文字を除外する場合は、ピリオド文字を追加の区切り文字として追加できます。 その方法を次の例に示します。

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#2)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="2":::

部分文字列からピリオドは削除されましたが、今度は 2 つの余分な空の部分文字列が含まれるようになっています。 これらの空の部分文字列は、単語とそれに続くピリオドの間の部分文字列を表します。 結果の配列から空の部分文字列を省略するには、<xref:System.String.Split(System.Char[],System.StringSplitOptions)> のオーバーロードを呼び出し、`options` パラメーターとして <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> を指定します。

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#3)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="3":::

## <a name="regular-expressions"></a>正規表現

文字列が固定パターンに準拠している場合は、正規表現を使用してその要素を抽出して処理できます。 たとえば、文字列の形式が "*数字* *オペランド* *数字*" の場合、[正規表現](regular-expressions.md)を使用して、文字列の要素を抽出して処理できます。 次に例を示します。

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="1":::

`(\d+)\s+([-+*/])\s+(\d+)` という正規表現パターンは、次のように定義されます。

|Pattern|説明|
|-------------|-----------------|
|`(\d+)`|1 個以上の 10 進数と一致します。 これが最初のキャプチャ グループです。|
|`\s+`|1 つ以上の空白文字と一致します。|
|`([-+*/])`|算術演算子の記号 (+、-、*、/) と一致します。 これが 2 番目のキャプチャ グループです。|
|`\s+`|1 つ以上の空白文字と一致します。|
|`(\d+)`|1 個以上の 10 進数と一致します。 これが 3 番目のキャプチャ グループです。|

また、正規表現を使用して、固定の文字セットではなく、パターンに基づいて文字列から部分文字列を抽出することもできます。 これは、次のいずれかの条件が発生するときの一般的なシナリオです。

- 1 つ以上の区切り文字が、<xref:System.String> インスタンスの区切り記号として "*常に*" 使用されるとは限りません。

- 区切り文字のシーケンスと数が、可変または不明です。

たとえば、<xref:System.String.Split%2A> メソッドを使用して、次の文字列を分割することはできません。これは、`\n` (改行) 文字の数が可変であり、常に区切り記号として機能しないためです。

```text
[This is captured\ntext.]\n\n[\n[This is more captured text.]\n]
\n[Some more captured text:\n   Option1\n   Option2][Terse text.]
```

次の例に示すように、正規表現を使用すると、この文字列を簡単に分割できます。

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="2" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="2":::

`\[([^\[\]]+)\]` という正規表現パターンは、次のように定義されます。

|Pattern|説明|
|-------------|-----------------|
|`\[`|左角かっこと一致します。|
|`([^\[\]]+)`|左または右の角かっこではない任意の文字と 1 回以上一致します。 これが最初のキャプチャ グループです。|
|`\]`|右角かっこと一致します。|

<xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> メソッドは <xref:System.String.Split%2A?displayProperty=nameWithType> とほぼ同じですが、固定文字セットではなく正規表現パターンに基づいて文字列を分割する点が異なります。 たとえば、次の例では、<xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> メソッドを使用して、ハイフンと他の文字のさまざまな組み合わせで区切られた部分文字列が含まれる文字列を分割します。

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="3" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="3":::

`\s-\s?[+*]?\s?-\s` という正規表現パターンは、次のように定義されます。

|Pattern|説明|
|-------------|-----------------|
|`\s-`|空白文字の後にハイフンが続くパターンに一致します。|
|`\s?`|0 個または 1 個の空白文字と一致します。|
|`[+*]?`|\+ または * のいずれかの文字の 0 回または 1 回の出現に一致します。|
|`\s?`|0 個または 1 個の空白文字と一致します。|
|`-\s`|ハイフンの後に空白文字が続くパターンに一致します。|

## <a name="stringindexof-and-stringsubstring-methods"></a>String.IndexOf メソッドと String.Substring メソッド

文字列内のすべての部分文字列に関心があるわけではない場合は、一致が始まる位置のインデックスを返す文字列比較メソッドのいずれかを使用することをお勧めします。 その後、<xref:System.String.Substring%2A> メソッドを呼び出して、必要な部分文字列を抽出できます。 次のような文字列比較メソッドがあります。

- <xref:System.String.IndexOf%2A>。文字列インスタンス内で文字または文字列が最初に出現する位置の 0 から始まるインデックスを返します。

- <xref:System.String.IndexOfAny%2A>。文字配列内で任意の文字が最初に出現する位置の、現在の文字列インスタンス内での 0 から始まるインデックスを返します。

- <xref:System.String.LastIndexOf%2A>。文字列インスタンス内で文字または文字列が最後に出現する位置の 0 から始まるインデックスを返します。

- <xref:System.String.LastIndexOfAny%2A>。文字配列内で任意の文字が最後に出現する位置の、現在の文字列インスタンス内での 0 から始まるインデックスを返します。

次の例では、<xref:System.String.IndexOf%2A> メソッドを使用して、文字列内のピリオドを検索します。 次に、<xref:System.String.Substring%2A> メソッドを使用して完全な文を返します。

:::code language="csharp" source="snippets/parse-strings/csharp/indexof.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/indexof.vb" id="1":::

## <a name="see-also"></a>関連項目

- [.NET の基本的な文字列操作](basic-string-operations.md)
- [.NET 正規表現](regular-expressions.md)
- [C# で String.Split を使用して文字列を解析する方法](../../csharp/how-to/parse-strings-using-split.md)
