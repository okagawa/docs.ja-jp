---
title: コード品質ルールの構成オプション
description: コード品質ルールの追加構成オプションを指定する方法について説明します。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 2721d4e8fda6012b304637477c3618ee0ff2ea18
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752068"
---
# <a name="code-quality-rule-configuration-options"></a>コード品質ルールの構成オプション

*コード品質* ルールには、[重要度を構成する](configuration-options.md#severity-level)だけでなく、追加の構成オプションがあります。 たとえば、各コード品質アナライザーは、コードベースの特定の部分にのみ適用するように構成できます。 これらのオプションを指定するには、キーと値のペアを同じファイルに追加します。このファイルには、 [EditorConfig](https://editorconfig.org) 規則の重大度と全般的なエディターの基本設定を指定します。

## <a name="option-scopes"></a>オプションスコープ

各 [調整] オプションは、ルールのカテゴリ (セキュリティや設計など)、または特定のルールに対して、すべてのルールに対して構成できます。

### <a name="all-rules"></a>すべてのルール

*すべて* のルールのオプションを構成するための構文は次のとおりです。

|構文|例|
|-|-|
| dotnet_code_quality。OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>ルールのカテゴリ

[ルールの *カテゴリ*](categories.md)のオプションを構成するための構文は次のとおりです。

|構文|例|
|-|-|
| dotnet_code_quality。RuleCategory OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>特定のルール

*特定* のルールのオプションを構成するための構文は次のとおりです。

|構文|例|
|-|-|
| dotnet_code_quality。RuleId OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="options"></a>オプション

ここでは、使用可能なオプションの一部を示します。 使用可能なオプションの完全な一覧については、「 [Analyzer の構成](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)」を参照してください。

### <a name="api_surface"></a>api_surface

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| 分析する API サーフェイスの部分 | `public`<br/>`internal` または `friend`<br/>`private`<br/>`all`<br/><br/>複数の値はコンマ (,) で区切ります | `public` | [CA1000](quality-rules/ca1000.md) [CA1003](quality-rules/ca1003.md) [CA1008](quality-rules/ca1008.md) [CA1010](quality-rules/ca1010.md)<br/>[CA1012](quality-rules/ca1012.md) [CA1024](quality-rules/ca1024.md) [CA1027](quality-rules/ca1027.md) [CA1028](quality-rules/ca1028.md)<br/>[CA1030](quality-rules/ca1030.md) [CA1036](quality-rules/ca1036.md) [CA1040](quality-rules/ca1040.md) [CA1041](quality-rules/ca1041.md)<br/>[CA1043](quality-rules/ca1043.md) [CA1044](quality-rules/ca1044.md) [CA1051](quality-rules/ca1051.md) [CA1052](quality-rules/ca1052.md)<br/>[CA1054](quality-rules/ca1054.md) [CA1055](quality-rules/ca1055.md) [CA1056](quality-rules/ca1056.md) [CA1058](quality-rules/ca1058.md)<br/>[CA1063](quality-rules/ca1063.md) [CA1708](quality-rules/ca1708.md) [CA1710](quality-rules/ca1710.md) [CA1711](quality-rules/ca1711.md)<br/>[CA1714](quality-rules/ca1714.md) [CA1715](quality-rules/ca1715.md) [CA1716](quality-rules/ca1716.md) [CA1717](quality-rules/ca1717.md)<br/>[CA1720](quality-rules/ca1720.md) [CA1721](quality-rules/ca1721.md) [CA1725](quality-rules/ca1725.md) [CA1801](quality-rules/ca1801.md)<br/>[CA1802](quality-rules/ca1802.md) [CA1815](quality-rules/ca1815.md) [CA1819](quality-rules/ca1819.md) [CA2217](quality-rules/ca2217.md)<br/>[CA2225](quality-rules/ca2225.md) [CA2226](quality-rules/ca2226.md) [CA2231](quality-rules/ca2231.md) [CA2234](quality-rules/ca2234.md)<br/>|

### <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| 値を返さない非同期メソッドを無視するかどうか | `true`<br/>`false` | `false` | [CA2007](quality-rules/ca2007.md) |

> [!NOTE]
> このオプションは `skip_async_void_methods` 、以前のバージョンで名前が付けられていました。

### <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| 1文字の [型パラメーター](../../csharp/programming-guide/generics/generic-type-parameters.md) をルールから除外するかどうか (例 `S` :) `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](quality-rules/ca1715.md) |

> [!NOTE]
> このオプションは `allow_single_letter_type_parameters` 、以前のバージョンで名前が付けられていました。

### <a name="output_kind"></a>output_kind

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| この型のアセンブリを生成するプロジェクト内のコードを分析する必要があることを指定します。 | 列挙体の1つまたは複数のフィールド <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>複数の値はコンマ (,) で区切ります | すべての出力の種類 | [CA2007](quality-rules/ca2007.md) |

### <a name="required_modifiers"></a>required_modifiers

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| 分析する必要がある Api の必須の修飾子を指定します | 以下の許可された修飾子テーブルの1つ以上の値<br/><br/>複数の値はコンマ (,) で区切ります | 各規則に依存 | [CA1802](quality-rules/ca1802.md) |

| 許可される修飾子 | まとめ |
| --- | --- |
| `none` | 修飾子の要件はありません |
| `static` または `Shared` | `static`(Visual Basic) として宣言する必要があります `Shared` 。 |
| `const` | はとして宣言する必要があります。 `const` |
| `readonly` | はとして宣言する必要があります。 `readonly` |
| `abstract` | はとして宣言する必要があります。 `abstract` |
| `virtual` | はとして宣言する必要があります。 `virtual` |
| `override` | はとして宣言する必要があります。 `override` |
| `sealed` | はとして宣言する必要があります。 `sealed` |
| `extern` | はとして宣言する必要があります。 `extern` |
| `async` | はとして宣言する必要があります。 `async` |

### <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| 拡張メソッドのパラメーターの分析をスキップするかどうか `this` | `true`<br/>`false` | `false` | [CA1062](quality-rules/ca1062.md) |

### <a name="null_check_validation_methods"></a>null_check_validation_methods

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| メソッドに渡された引数が null でないことを検証する null チェック検証メソッドの名前 | 許可するメソッド名の形式 (で区切る `|` ):<br/> -メソッド名のみ (包含する型または名前空間に関係なく、という名前のすべてのメソッドが含まれます)<br/> -省略可能なプレフィックスを持つシンボルの[ドキュメント ID 形式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)の完全修飾名 `M:` | なし | [CA1062](quality-rules/ca1062.md) |

### <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| 追加の文字列書式指定メソッドの名前 | 許可するメソッド名の形式 (で区切る `|` ):<br/> -メソッド名のみ (包含する型または名前空間に関係なく、という名前のすべてのメソッドが含まれます)<br/> -省略可能なプレフィックスを持つシンボルの[ドキュメント ID 形式](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)の完全修飾名 `M:` | なし | [CA2241](quality-rules/ca2241.md) |

### <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| 型の名前 (型とそのすべての派生型が分析に対して除外される) | 使用できるシンボル名の形式 (で区切る `|` ):<br/> -型名のみ (包含する型または名前空間に関係なく、名前を持つすべての型を含む)<br/> -省略可能なプレフィックスを持つシンボルの[ドキュメント ID 形式](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)の完全修飾名 `T:` | なし | [CA1303](quality-rules/ca1303.md) |

### <a name="excluded_symbol_names"></a>excluded_symbol_names

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| 分析に対して除外されるシンボルの名前 | 使用できるシンボル名の形式 (で区切る `|` ):<br/> -シンボル名のみ (包含する型または名前空間に関係なく、名前の付いたすべての記号が含まれます)<br/> -シンボルの [ドキュメント ID 形式](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)の完全修飾名。 各シンボル名には、 `M:` メソッドのプレフィックス、 `T:` 型のプレフィックス、 `N:` 名前空間のプレフィックスなど、記号の種類のプレフィックスが必要です。<br/> - `.ctor` コンストラクターと `.cctor` 静的コンストラクターの場合 | なし | [CA1062](quality-rules/ca1062.md) [CA1303](quality-rules/ca1303.md) [CA2000](quality-rules/ca2000.md) [CA2100](quality-rules/ca2100.md) [CA2301](quality-rules/ca2301.md) [CA2302](quality-rules/ca2302.md)<br/>[CA2311](quality-rules/ca2311.md) [CA2312](quality-rules/ca2312.md) [CA2321](quality-rules/ca2321.md) [CA2322](quality-rules/ca2322.md) [CA2327](quality-rules/ca2327.md) [CA2328](quality-rules/ca2328.md)<br/>[CA2329](quality-rules/ca2329.md) [CA2330](quality-rules/ca2330.md) [CA3001](quality-rules/ca3001.md) [CA3002](quality-rules/ca3002.md) [CA3003](quality-rules/ca3003.md) [CA3004](quality-rules/ca3004.md)<br/>[CA3005](quality-rules/ca3005.md) [CA3006](quality-rules/ca3006.md) [CA3007](quality-rules/ca3007.md) [CA3008](quality-rules/ca3008.md) [CA3009](quality-rules/ca3009.md) [CA3010](quality-rules/ca3010.md)<br/>[CA3011](quality-rules/ca3011.md) [CA3012](quality-rules/ca3012.md) [CA5361](quality-rules/ca5361.md) CA5376 CA5377 [CA5378](quality-rules/ca5378.md)<br/>[CA5380](quality-rules/ca5380.md) [CA5381](quality-rules/ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](quality-rules/ca5389.md) CA5390 |

### <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| 説明 | 使用できる値 | 既定値 | 構成可能な規則 |
| - | - | - | - |
| 分析のコンテキストで禁止されているシンボルの名前 | 使用できるシンボル名の形式 (で区切る `|` ):<br/> -シンボル名のみ (包含する型または名前空間に関係なく、名前の付いたすべての記号が含まれます)<br/> -シンボルの [ドキュメント ID 形式](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)の完全修飾名。 各シンボル名には、 `M:` メソッドのプレフィックス、 `T:` 型のプレフィックス、 `N:` 名前空間のプレフィックスなど、記号の種類のプレフィックスが必要です。<br/> - `.ctor` コンストラクターと `.cctor` 静的コンストラクターの場合 | なし | [CA1031](quality-rules/ca1031.md) |
