---
title: .NET でのコード分析
titleSuffix: ''
description: .NET SDK のソースコード分析について説明します。
ms.date: 08/22/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: 8efac4d5e3fddcb9fdc6e08bcc933f2776420ced
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739975"
---
# <a name="overview-of-net-source-code-analysis"></a>.NET ソース コード分析の概要

.NET のコンパイラ プラットフォーム (Roslyn) アナライザーでは、お使いの C# または Visual Basic コードについて、コード品質やコード スタイルに関する問題を検査できます。 .NET 5.0 以降、これらのアナライザーは .NET SDK に含まれるようになりました。 .NET 5 + SDK に移行しない場合、または NuGet パッケージベースのモデルを使用する場合は、nuget パッケージでアナライザーを使用することもでき `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)ます。 オンデマンドバージョン更新には、パッケージベースのモデルを使用することをお勧めします。

> [!NOTE]
> .NET アナライザーは、ターゲットプラットフォームに依存しません。 つまり、プロジェクトは特定の .NET プラットフォームを対象にする必要がありません。 アナライザーは、、、など、以前のバージョンの .NET を対象とするプロジェクトに対して機能し `net5.0` `netcoreapp` `netstandard` `net472` ます。

- [コード品質分析 ("CAxxxx" ルール)](#code-quality-analysis)
- [コードスタイル分析 ("Ide Xxxx" 規則)](#code-style-analysis)

ルール違反が analyzer によって検出されると、各ルールの [構成](configuration-options.md)方法に応じて、候補、警告、またはエラーとして報告されます。 コード分析違反は、コンパイラエラーと区別するために "CA" または "IDE" というプレフィックスで示されます。

> [!TIP]
>
> - [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [roslの ator](https://www.nuget.org/packages/Roslynator.Analyzers/)、 [Xunit](https://www.nuget.org/packages/xunit.analyzers/) [Analyzer、sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)などのサードパーティ製アナライザーをインストールすることもできます。
> - Visual Studio を使用している場合は、多くのアナライザールールに関連付けられている *コード修正プログラム* を適用して、問題を修正できます。 コード修正は、電球アイコンメニューに表示されます。

## <a name="code-quality-analysis"></a>コード品質の分析

_コード品質分析 ("CA") 規則_ は、セキュリティ、パフォーマンス、設計などの問題について、C# または Visual Basic コードを検査します。 .NET 5.0 以降を対象とするプロジェクトでは、既定で分析が有効になっています。 以前のバージョンの .NET を対象とするプロジェクトでは、 [Enablenetanalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティをに設定することにより、コード分析を有効にすることができ `true` ます。 をに設定することにより、プロジェクトのコード分析を無効にすることもでき `EnableNETAnalyzers` `false` ます。

> [!TIP]
> Visual Studio では、プロジェクトプロパティウィンドウを使用してコード分析を有効または無効にすることができます。 プロジェクトプロパティウィンドウにアクセスするにはソリューションエクスプローラー内のプロジェクトを右クリックし、[ **プロパティ**] を選択します。 次に、[ **コード分析** ] タブを選択し、[ **.Net アナライザーを有効** にする] チェックボックスをオンまたはオフにします。

### <a name="enabled-rules"></a>有効なルール

.NET 5.0 Preview 8 では、既定で次のルールが有効になっています。

| 診断 ID | カテゴリ | 重大度 | 説明 |
| - | - | - | - |
| [CA1416](/visualstudio/code-quality/ca1416) | 相互運用性 | 警告 | プラットフォーム互換性アナライザー |
| [CA1417](/visualstudio/code-quality/ca1417) | 相互運用性 | 警告 | `OutAttribute`P/invoke に文字列パラメーターを使用しない |
| [CA1831](/visualstudio/code-quality/ca1831) | パフォーマンス | 警告 | `AsSpan`必要に応じて、範囲ベースのインデクサーの代わりに文字列を使用します。 |
| [CA2013](/visualstudio/code-quality/ca2013) | [信頼性] | 警告 | `ReferenceEquals`値型では使用しない |
| [CA2014](/visualstudio/code-quality/ca2014) | [信頼性] | 警告 | In ループを使用しない `stackalloc` |
| [CA2015](/visualstudio/code-quality/ca2015) | [信頼性] | 警告 | から派生した型にはファイナライザーを定義しないでください。 <xref:System.Buffers.MemoryManager%601> |
| [CA2200](/visualstudio/code-quality/ca2200) | 使用 | 警告 | スタック詳細を保持するために再度スローします
| [CA2247](/visualstudio/code-quality/ca2247) | 使用 | 警告 | Taskのソースコンストラクターに渡される引数は、ではなく列挙型にする必要があり <xref:System.Threading.Tasks.TaskCreationOptions> ます <xref:System.Threading.Tasks.TaskContinuationOptions> |

これらのルールを無効にするか、エラーに昇格するように、これらのルールの重大度を変更することができます。

使用可能なコード品質ルールの完全な一覧については、「 [コード品質ルール](quality-rules/index.md)」を参照してください。

### <a name="enable-additional-rules"></a>追加のルールを有効にする

.NET 5.0 RC2 以降、.NET SDK には、すべての ["CA" コード品質ルール](/visualstudio/code-quality/code-analysis-for-managed-code-warnings)が付属しています。 各 .NET SDK バージョンに含まれる規則の完全な一覧については、「 [analyzer のリリース](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)」を参照してください。

#### <a name="default-analysis-mode"></a>既定の分析モード

既定の分析モードでは、一部のルールがビルド警告として [既定で有効になっ](#enabled-rules) ています。 他の規則の中には、既定では Visual Studio IDE の提案としてのみ有効になっているものがあります。 残りのルールは、既定では無効になっています。 ルール [の完全な一覧](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md) には、各ルールの既定の重要度と、既定の分析モードでルールが既定で有効になっているかどうかが含まれます。

#### <a name="custom-analysis-mode"></a>カスタム分析モード

個々のルールまたはルールのカテゴリを有効または無効にするように、 [コード分析ルールを構成](configuration-options.md) することができます。 さらに、 [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) プロパティを使用して、次のいずれかのカスタム分析モードに切り替えることができます。

- _アグレッシブ_ モードまたは _オプトアウト_ モード: 既定では、すべてのルールがビルド警告として有効になります。 個々のルールを選択的に[オプトアウト](configuration-options.md)して無効にすることができます。
- _控えめ_ または _オプトイン_ モード: 既定では、すべての規則が無効になっています。 個々のルールを選択的に[オプトイン](configuration-options.md)して有効にすることができます。

### <a name="treat-warnings-as-errors"></a>警告をエラーとして扱う

`-warnaserror`プロジェクトをビルドするときにフラグを使用すると、コード分析のすべての警告もエラーとして扱われます。 コード品質警告 (CAxxxx) がの存在でエラーとして扱われないようにするには `-warnaserror` 、 `CodeAnalysisTreatWarningsAsErrors` プロジェクトファイルで MSBuild プロパティをに設定し `false` ます。

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

コード分析の警告は引き続き表示されますが、ビルドが破損することはありません。

### <a name="latest-updates"></a>最新の更新プログラム

既定では、新しいバージョンの .NET SDK にアップグレードするときに、最新のコード分析規則と既定の規則の重大度を取得します。 この動作が望ましくない場合、たとえば、新しいルールが有効になっていないか無効になっていることを確認する場合は、次のいずれかの方法でオーバーライドできます。

- `AnalysisLevel`MSBuild プロパティを特定の値に設定して、そのセットに警告をロックします。 新しい SDK にアップグレードすると、これらの警告のバグ修正が引き続き行われますが、新しい警告は有効になりません。また、既存の警告は無効になりません。 たとえば、.NET SDK のバージョン5.0 に付属するルールのセットをロックするには、プロジェクトファイルに次のエントリを追加します。

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > プロパティの既定値 `AnalysisLevel` はです `latest` 。これは、.net SDK の新しいバージョンに移行するときに、常に最新のコード分析規則を取得することを意味します。

  詳細については、および使用可能な値の一覧については、「 [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel)」を参照してください。

- .NET SDK の更新プログラムから規則の更新を分離するには、 [Microsoft Codeanalysis NuGet パッケージ](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) をインストールします。 パッケージをインストールすると、組み込みの SDK アナライザーが無効になり、SDK に NuGet パッケージよりも新しいバージョンの analyzer アセンブリが含まれている場合は、ビルドの警告が生成されます。

## <a name="code-style-analysis"></a>コードスタイルの分析

[コードスタイル分析](/visualstudio/ide/editorconfig-code-style-settings-reference) ("ide xxxx" 規則) を使用すると、コードベースで一貫性のあるコードスタイルを定義および維持できます。 既定の設定は次のとおりです。

- コマンドラインビルド: コマンドラインビルドのすべての .NET プロジェクトに対して、コードスタイル分析が既定で無効になっています。
- Visual Studio: コードスタイル分析は、Visual Studio 内のすべての .NET プロジェクトに対して、 [コードリファクタリングクイックアクション](/visualstudio/ide/code-generation-in-visual-studio)として既定で有効になっています。

.NET 5.0 RC2 を開始すると、コマンドラインと Visual Studio の両方でビルドに対してコードスタイル分析を有効にすることができます。 コードスタイル違反は、"IDE" プレフィックスが付いた警告またはエラーとして表示されます。 これにより、ビルド時に一貫したコードスタイルを適用できます。

> [!NOTE]
> コードスタイル分析機能は試験段階であり、.NET 5 リリースと .NET 6 リリース間で変更される可能性があります。

ビルドでコードスタイル分析を有効にする手順:

1. MSBuild プロパティ [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) をに設定し `true` ます。

1. *Editorconfig* ファイルで、ビルド時に実行する各 "IDE" コードスタイルルールを警告またはエラーとして [構成](configuration-options.md)します。 次に例を示します。

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   または、[スタイル] カテゴリ全体を警告またはエラーとして構成し、既定では、ビルドで実行しない規則を選択的にオフにすることができます。 次に例を示します。

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

## <a name="suppress-a-warning"></a>警告の非表示

規則違反を抑制するには、その規則 ID の重大度オプションを `none` EditorConfig ファイルでに設定します。 次に例を示します。

```ini
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio には、コード分析規則からの警告を抑制するための追加の方法が用意されています。 詳細については、「 [違反の抑制](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)」を参照してください。

規則の重大度の詳細については、「 [規則の重要度の構成](configuration-options.md#severity-level)」を参照してください。

## <a name="see-also"></a>こちらもご覧ください

- [コード品質分析ルールのリファレンス](quality-rules/index.md)
- [コードスタイル分析規則のリファレンス](style-rules/index.md)
- [Visual Studio でのコード分析](/visualstudio/code-quality/roslyn-analyzers-overview)
- [.NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md)
- [チュートリアル: 最初のアナライザーとコード修正を作成する](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
