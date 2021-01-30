---
title: コード分析規則の構成ファイル
description: コード分析規則を構成するためのさまざまな構成ファイルについて説明します。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: b98fdd48f2373bd23fcd3273834860a60c682969
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216383"
---
# <a name="configuration-files-for-code-analysis-rules"></a>コード分析規則の構成ファイル

コード分析規則には、さまざまな [構成オプション](configuration-options.md)があります。 これらのオプションは、次のいずれかのアナライザー構成ファイルのキーと値のペアとして指定します。

- [EditorConfig](#editorconfig) ファイル: ファイルベースまたはフォルダーベースの構成オプション。
- [Global AnalyzerConfig](#global-analyzerconfig) File: プロジェクトレベルの構成オプション。 プロジェクトフォルダーの外部に存在するプロジェクトファイルがある場合に便利です。

## EditorConfig

[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) ファイルは、特定の **ソースファイルまたはフォルダーに適用されるオプション** を提供するために使用されます。 オプションは、該当するファイルとフォルダーを識別するために、セクションヘッダーの下に配置されます。 構成する各規則のエントリを追加し、対応するファイル拡張子セクションの下に配置します。たとえば、のように `[*.cs]` します。

```ini
[*.cs]
<option_name> = <option_value>
```

上の例で `[*.cs]` は、は editorconfig セクションヘッダーで、現在のフォルダー内のファイル拡張子を持つすべての C# ファイル `.cs` (サブフォルダーを含む) を選択します。 後続のエントリは、 `<option_name> = <option_value>` すべての C# ファイルに適用されるアナライザーオプションです。

ファイル規則は、 EditorConfig 対応するディレクトリに配置することによって、フォルダー、プロジェクト、またはリポジトリ全体に適用できます。 これらのオプションは、ビルド時に分析を実行するときと、Visual Studio でコードを編集するときに適用されます。

インデントサイズや末尾の空白文字を削除するかどうかなど、エディターの設定に既存の *editorconfig* ファイルがある場合は、コード分析の構成オプションを同じファイルに配置できます。

> [!TIP]
> Visual Studio には、これらのファイルの1つをプロジェクトに簡単に追加できるようにする、editorconfig 項目テンプレートが用意されてい *ます。* 詳細については、「 [ EditorConfig プロジェクトへのファイルの追加](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project)」を参照してください。

### <a name="example"></a>例

EditorConfigオプションとルールの重要度を構成するファイルの例を次に示します。

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a>グローバル AnalyzerConfig

.NET 5 SDK (Visual Studio 2019 バージョン16.8 以降でサポートされています) 以降では、グローバル _AnalyzerConfig_ ファイルを使用してアナライザーオプションを構成することもできます。 これらのファイルは、ファイル名やファイルパスに関係なく、 **プロジェクト内のすべてのソースファイルに適用されるオプション** を提供するために使用されます。

ファイルとは異なり [EditorConfig](#editorconfig) 、グローバル構成ファイルを使用して、インデントサイズや末尾の空白をトリミングするかどうかなど、ide のエディタースタイル設定を構成することはできません。 代わりに、プロジェクトレベルのアナライザーの構成オプションを指定するために、純粋に設計されています。

### <a name="format"></a>フォーマット

EditorConfig該当するファイルとフォルダーを識別するためになどのセクションヘッダーを持つ必要があるファイルとは異なり `[*.cs]` 、グローバル AnalyzerConfig ファイルにはセクションヘッダーがありません。 代わりに、 `is_global = true` 通常のファイルと区別するために、フォームの最上位レベルのエントリが必要 EditorConfig です。 これは、ファイル内のすべてのオプションがプロジェクト全体に適用されることを示します。 例:

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a>名前を付ける

名前を付ける必要があるファイルとは異なり EditorConfig `.editorconfig` 、グローバル構成ファイルには、特定の名前や拡張子を付ける必要はありません。 ただし、これらのファイルにという名前を付けた場合、 `.globalconfig` サブフォルダーを含む現在のフォルダー内のすべての C# および Visual Basic プロジェクトに暗黙的に適用されます。 それ以外の場合は、 `GlobalAnalyzerConfigFiles` MSBuild プロジェクトファイルに項目を明示的に追加する必要があります。

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> ファイル名がの場合でも、最上位レベルのエントリ `is_global = true` が必要です `.globalconfig` 。

### <a name="example"></a>例

次に示すのは、プロジェクトレベルでオプションとルールの重要度を構成するグローバル AnalyzerConfig ファイルの例です。

```ini
# Top level entry required to mark this as a global AnalyzerConfig file
is_global = true

# NOTE: No section headers for configuration entries

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="precedence"></a>優先順位

EditorConfigファイルとグローバル AnalyzerConfig ファイルはどちらも、各オプションのキーと値のペアを指定します。 競合は、キーが同じで値が異なる複数のエントリが存在する場合に発生します。

### <a name="general-options"></a>[全般] オプション

オプション間で競合が発生した場合は、次の優先順位ルールを使用して競合を解決します。

- 同じ構成ファイル内のエントリが競合しています。ファイル内で後で表示されるエントリが優先されます。 これは、1つのファイル内のエントリ EditorConfig と、1つのグローバル AnalyzerConfig ファイル内のエントリの競合にも当てはまります。

- 2つのファイル内のエントリが競合してい EditorConfig ます。ファイルシステムのより深いファイル内のエントリがあるため、ファイル EditorConfig パスが長くなります。

- 2つのグローバル AnalyzerConfig ファイルで競合するエントリ: コンパイラの警告が報告され、両方のエントリが無視されます。

- ファイル内のエントリ EditorConfig とグローバル AnalyzerConfig ファイルが競合しています。ファイル内のエントリが優先され EditorConfig ます。

### <a name="severity-options"></a>重要度オプション

前の [一般優先順位の規則](#general-options) は、構成ファイルで指定されているすべてのオプションに適用されます。 [重要度の構成](configuration-options.md#severity-level)オプションについては、次の優先順位の規則が適用されます。

- コンパイラオプションとしてコマンドラインで指定された重大度オプション ( `/nowarn` または `/warnaserror` ) は、とグローバル AnalyzerConfig ファイルで指定された [重大度構成](configuration-options.md#severity-level) オプションを常にオーバーライドし EditorConfig ます。

- 重大度オプションは、 [ルールセット](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) ファイルと共に指定することもできます。 ただし、およびグローバル AnalyzerConfig ファイルを優先する場合は、ルールセットファイルが非推奨とされ EditorConfig ます。 [ルールセットファイルを同等の EditorConfig ファイルに変換](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file)することをお勧めします。 ルールセットファイルとグローバル AnalyzerConfig ファイルの競合する重要度エントリの優先順位 EditorConfig は _定義_ されていません。

- 異なるキーを持つ関連する重大度オプションの優先順位規則については、「 [コード分析の構成オプション](configuration-options.md#precedence)」を参照してください。たとえば、1つの規則に対して異なる重大度が指定されている場合などです。

## <a name="see-also"></a>関連項目

- [EditorConfig vs global AnalyzerConfig のデザインの問題](https://github.com/dotnet/roslyn/issues/47707)
