---
title: コードスタイルの名前付け規則
description: コード要素に名前を付けるための .NET コードスタイル規則について説明します。
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE1006
- naming rules
helpviewer_keywords:
- IDE1006
- naming code style rules [EditorConfig]
- naming rules
- EditorConfig naming conventions
ms.openlocfilehash: df2cbc8299d853b5730bc39eb25c6f97b6575655
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429209"
---
# <a name="naming-rules"></a>名前付け規則

ファイルでは `.editorconfig` 、クラス、プロパティ、メソッドなどの .net プログラミング言語コード要素の名前付け方法を指定し、適用する **名前付け規則** を定義でき &mdash; &mdash; ます。 たとえば、パブリックメンバーを大文字にする必要がある場合や、プライベートフィールドの先頭がであることを指定でき `_` ます。

名前付け規則には、次の3つのコンポーネントがあります。

* 規則が適用される **シンボルグループ** (パブリックメンバー、プライベートフィールドなど)。
* 規則に関連付ける名前 **付けスタイル** 。たとえば、名前が大文字であるか、アンダースコアで始まる必要があります。
* 規則を適用するための重大度。

まず、シンボルグループと名前付けスタイルを指定し、それぞれにタイトルを付ける必要があります。 次に、すべてをリンクする名前付け規則を指定します。

## <a name="general-syntax"></a>一般的な構文

名前付け規則、シンボルグループ、または名前付けスタイルを定義するには、次の構文を使用して1つ以上のプロパティを設定します。

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

各プロパティは一度だけ設定する必要がありますが、一部の設定では複数のコンマ区切りの値を使用できます。

プロパティの順序は重要ではありません。

### \<kind>

**\<kind>** 定義する &mdash; 名前付け規則、シンボルグループ、または名前付けスタイルの要素の種類を指定し &mdash; ます。次のいずれかを指定する必要があります。

| のプロパティを設定するには | 値を使用する \<kind> | 例 |
| --- | --- | -- |
| 名前付け規則 | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| シンボルグループ | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| 名前付けスタイル | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

&mdash;次のセクションで説明するように、定義の[名前付け規則](#naming-rule-properties)、[シンボルグループ](#symbol-group-properties)、または[名前付けスタイル](#naming-style-properties)の各種類 &mdash; には、独自のサポートされるプロパティがあります。

### \<title>

**\<title>** 複数のプロパティ設定を1つの定義に関連付けるために選択するわかりやすい名前を指定します。 たとえば、次のプロパティでは、とという2つのシンボルグループ定義が生成され `interface` `types` ます。それぞれに2つのプロパティが設定されています。

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a>名前付け規則のプロパティ

ルールを有効にするには、すべての名前付けルールプロパティが必要です。

| プロパティ | [説明] |
| -- | -- |
| `symbols` | シンボルグループのタイトル。このグループのシンボルには名前付け規則が適用されます |
| `style` | この規則に関連付ける必要がある名前付けスタイルのタイトル |
| `severity` |  名前付け規則を適用するための重大度を設定します。 関連する値を、使用可能な [重大度レベル](../configuration-options.md#severity-level)のいずれかに設定します。<sup>1</sup> |

**注:**

1. 名前付け規則内の重要度の指定は、Visual Studio などの開発 Ide 内でのみ尊重されます。 この設定は、C# または VB コンパイラで認識されないため、ビルド時には尊重されません。 ビルドに名前付けスタイルルールを適用するには、代わりに [コード規則の重要度の構成](#rule-id-ide1006-naming-rule-violation)を使用して重大度を設定する必要があります。 詳細については、[こちらの GitHub の問題](https://github.com/dotnet/roslyn/issues/44201)のページを参照してください。

## <a name="symbol-group-properties"></a>シンボルグループのプロパティ

シンボルグループの次のプロパティを設定して、グループに含めるシンボルを制限できます。 1つのプロパティに複数の値を指定するには、値をコンマで区切ります。

| プロパティ | 説明 | 使用できる値 | 必須 |
| -- | -- | -- | -- |
| `applicable_kinds` | グループ<sup>1</sup>のシンボルの種類 | `*`(この値を使用すると、すべてのシンボルが指定されます)<br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | はい |
| `applicable_accessibilities` | グループ内のシンボルのアクセシビリティレベル | `*`(この値を使用すると、すべてのアクセシビリティ レベルが指定されます)<br/>`public`<br/>`internal` または `friend`<br/>`private`<br/>`protected`<br/>`protected_internal` または `protected_friend`<br/>`private_protected`<br/>`local` (メソッド内で定義されたシンボルの場合) | はい |
| `required_modifiers` | 指定した _すべて_ の修飾子を持つシンボルのみ一致 <sup>2</sup> | `abstract` または `must_inherit`<br/>`async`<br/>`const`<br/>`readonly`<br/>`static` または `shared` <sup>3</sup> | いいえ |

**注:**

1. 組メンバーは現在ではサポートされていません `applicable_kinds` 。
2. シンボルグループは、プロパティ内の _すべて_ の修飾子と一致し `required_modifiers` ます。  このプロパティを省略した場合、一致には特定の修飾子は必要ありません。 このことは、この規則が適用されるかどうかに、シンボルの修飾子が影響を及ぼさないことを意味します。
3. グループのプロパティにまたはが含まれている場合は、暗黙的に使用される `static` `shared` ため、グループに `required_modifiers` もシンボルが含まれ `const` `static` / `Shared` ます。 ただし、 `static` 名前付け規則をシンボルに適用しない場合は、 `const` のシンボルグループを使用して新しい名前付け規則を作成でき `const` ます。

## <a name="naming-style-properties"></a>名前付けスタイルのプロパティ

名前付けスタイルは、規則に適用する規則を定義します。 次に例を示します。

* を大文字にする `PascalCase`
* で始まる `m_`
* で終わる `_g`
* 単語の区切り `__`

名前付けスタイルには、次のプロパティを設定できます。

| プロパティ | 説明 | 使用できる値 | 必須 |
| -- | -- | -- | -- |
| `capitalization` | シンボル内の単語の大文字/小文字のスタイル | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | 可<sup>1</sup> |
| `required_prefix` | 次の文字で始まる必要があります。 | | いいえ |
| `required_suffix` | 次の文字で終わる必要があります。 | | いいえ |
| `word_separator` | シンボル内の単語は、この文字で区切る必要があります。 | | いいえ |

**注:**

1. 名前付けスタイルの一部として大文字/小文字スタイルを指定する必要があります。そうしないと、名前付けスタイルは無視される可能性があります。

## <a name="rule-order"></a>ルールの順序

EditorConfig ファイルで名前付け規則を定義する順序は問題ではありません。 名前付け規則は、規則自体の定義に従って自動的に並べ替えられます。 [EditorConfig 言語サービス拡張機能](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)では、EditorConfig ファイルを分析して、ファイルでの規則の順序が実行時にコンパイラで使用される順序と異なる場合に報告できます。

> [!NOTE]
>
> Visual studio 2019 バージョン16.2 より前のバージョンの Visual Studio を使用している場合、EditorConfig ファイルでは、名前付け規則を最も限定的なものから最も限定的なものに順番に並べ替える必要があります。 適用可能な最初に検出されたルールのみが適用されます。 ただし、同じ名前のルールの "*プロパティ*" が複数ある場合は、その名前の最も最近見つかったプロパティが優先されます。 詳細については、「[File hierarchy and precedence (ファイルの階層と優先順位)](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence)」を参照してください。

## <a name="default-naming-styles"></a>既定の名前付けスタイル

カスタム名前付け規則を指定しない場合は、次の既定のスタイルが使用されます。

- アクセシビリティが `public`、`private`、`internal`、`protected`、または `protected_internal` であるクラス、構造体、列挙型、プロパティ、およびイベントでは、既定の名前付けスタイルはパスカル ケースです。

- アクセシビリティが `public`、`private`、`internal`、`protected`、または `protected_internal` であるインターフェイスでは、既定の名前付けスタイルはパスカル ケースであり、プレフィックス **I** を付ける必要があります。

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a>コード規則 ID: `IDE1006 (Naming rule violation)`

すべての名前付けオプションには、ルール ID `IDE1006` とタイトルがあり `Naming rule violation` ます。 EditorConfig ファイルでは、次の構文を使用して、名前付け違反の重大度をグローバルに構成できます。

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

重大度値は、 `warning` `error` [ビルドで適用](../overview.md#code-style-analysis)される必要があります。 可能なすべての重要度の値については、「 [重大度レベル](../configuration-options.md#severity-level)」を参照してください。

## <a name="example"></a>例

次の *.editorconfig* ファイルには、パブリック プロパティ、メソッド、フィールド、イベント、デリゲートを大文字で入力する必要があることを指定した名前付け規則が含まれています。 この名前付け規則では、コンマを使用して個々のシンボル値を区切ることにより、規則を適用する複数の種類のシンボルを指定しています。

```ini
[*.{cs,vb}]

# Defining the 'public_symbols' symbol group
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

# Defining the `first_word_upper_case_style` naming style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

# Defining the `public_members_must_be_capitalized` naming rule, by setting the symbol group to the 'public symbols' symbol group,
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
# setting the naming style to the `first_word_upper_case_style` naming style,
dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
# and setting the severity.
dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

## <a name="see-also"></a>関連項目

- [言語規則](language-rules.md)
- [書式設定規則](formatting-rules.md)
- [Roslyn の名前付け規則](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [.NET コードスタイル規則のリファレンス](index.md)
