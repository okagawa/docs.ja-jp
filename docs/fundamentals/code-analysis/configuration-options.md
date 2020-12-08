---
title: コード分析規則の構成
description: アナライザーの構成ファイルでコード分析規則を構成する方法について説明します。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 4f7b392a2b066023fec75c5295bd94651654d645
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851791"
---
# <a name="configuration-options-for-code-analysis"></a>コード分析の構成オプション

コード分析規則には、さまざまな構成オプションがあります。 これらのオプションは、構文を使用して、 [アナライザー構成ファイル](configuration-files.md) のキーと値のペアとして指定され `<option key> = <option value>` ます。

最も一般的に構成するオプションは、 [ルールの重要度](#severity-level)です。 [コード品質ルール](quality-rules/index.md)や[コードスタイルルール](style-rules/index.md)など、すべてのアナライザールールの重大度レベルを構成することができます。 たとえば、警告としてルールを有効にするには、次のキーと値のペアをファイルに追加し EditorConfig ます。

`dotnet_diagnostic.<rule ID>.severity = warning`

ルールの動作をカスタマイズするための追加のオプションを構成することもできます。

- コード品質ルールには、ルールを適用する必要があるメソッド名など、動作を構成するための [追加のオプション](code-quality-rule-options.md) があります。
- コードスタイル規則には、 [カスタムコードスタイルオプション](code-style-rule-options.md)があります。
- サードパーティの analyzer ルールでは、独自の構成オプションを定義できます。カスタムキー名と値の形式を使用できます。

[Analyzer 構成ファイル](configuration-files.md)で特定のルールの重要度を構成するための構文は次のとおりです。

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a>[全般] オプション

これらのオプションは、コード分析全体に適用されます。 1つのルールまたは一連のルールのみに適用することはできません。

### <a name="exclude-generated-code"></a>生成されたコードを除外する

`generated_code = true | false`[構成ファイル](configuration-files.md)にエントリを追加することで、生成されたコードとして扱われる追加のファイルとフォルダーを構成できます。 .NET コードアナライザーの警告は、デザイナーで生成されたファイルなど、生成されたコードファイルでは役に立ちません。ユーザーは、このファイルを編集して違反を修正することはできません。 ほとんどの場合、コードアナライザーは生成されたコードファイルをスキップし、これらのファイルに対する違反を報告しません。

既定では、特定のファイル拡張子または自動生成されたファイルヘッダーを持つファイルは、生成されたコードファイルとして扱われます。 たとえば、またはで終わるファイル名 `.designer.cs` `.generated.cs` は、生成されたコードと見なされます。 この構成オプションを使用すると、追加の命名パターンを指定できます。

たとえば、名前がで終わるすべてのファイルを、 `.MyGenerated.cs` 生成されたコードとして扱うには、次のエントリを追加します。

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a>ルール固有のオプション

ルール固有のオプションは、1つのルール、一連のルール、またはすべてのルールに適用できます。 ルール固有のオプションは次のとおりです。

- [ルールの重大度レベル](#severity-level)
- [*コード品質* 規則に固有のオプション](code-quality-rule-options.md)

### <a name="severity-level"></a>重大度レベル

次の表は、 [コード品質](quality-rules/index.md) や [コードスタイル](style-rules/index.md) の規則など、すべてのアナライザーの規則に対して構成できるさまざまな規則の重大度を示しています。

| 重大度 | ビルド時の動作 |
|-|-|
| `error` | 違反はビルド *エラー* として表示され、ビルドが失敗します。|
| `warning` | 違反はビルドの *警告* として表示されますが、ビルドが失敗することはありません (警告をエラーとして扱うオプションが設定されていない場合)。 |
| `suggestion` | 違反は、Visual Studio IDE のビルド *メッセージ* および提案として表示されます。 |
| `silent` | 違反はユーザーに表示されません。 |
| `none` | 規則は完全に抑制されます。 |
| `default` | ルールの既定の重要度が使用されます。 |

> [!TIP]
> Visual Studio でのルールの重大度の詳細については、「 [重大度レベル](/visualstudio/ide/editorconfig-language-conventions#severity-levels)」を参照してください。

#### <a name="scope"></a>Scope

ルールの重要度を1つのルールに設定するには、次の構文を使用します。

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

アナライザールールのカテゴリに既定のルールの重要度を設定するには、次の構文を使用します。

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

すべてのアナライザールールの既定のルールの重要度を設定するには、次の構文を使用します。

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a>優先順位

同じ規則 ID に適用できる重要度の構成エントリが複数ある場合は、次の順序で優先順位が選択されます。

- ID による個々のルールのエントリは、カテゴリのエントリよりも優先されます。
- カテゴリのエントリは、すべてのアナライザールールのエントリよりも優先されます。

次の例を考えてみます。 [CA1822](/visualstudio/code-quality/ca1822) には "Performance" というカテゴリがあります。

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

前の例では、3つの重要度のエントリすべてが CA1822 に適用されます。 ただし、指定された優先順位規則を使用すると、最初の規則 ID ベースのエントリは次のエントリに優先します。 この例では、CA1822 の有効な重要度は `error` です。 "パフォーマンス" カテゴリ内のその他のすべてのルールの重要度はになり `warning` ます。

ファイルの優先順位の決定方法の詳細については、 [構成ファイルの記事の「優先順位」セクション](configuration-files.md#precedence)を参照してください。
