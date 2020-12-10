---
title: .NET でのコード分析
titleSuffix: ''
description: .NET SDK のソースコード分析について説明します。
ms.date: 12/04/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: 2f59b97de6f92e5a9bf927e1318286e400017dad
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009847"
---
# <a name="overview-of-net-source-code-analysis"></a>.NET ソース コード分析の概要

.NET のコンパイラ プラットフォーム (Roslyn) アナライザーでは、お使いの C# または Visual Basic コードについて、コード品質やコード スタイルに関する問題を検査できます。 .NET 5.0 以降、これらのアナライザーは .NET SDK に含まれており、個別にインストールする必要はありません。 プロジェクトが .NET 5 以降を対象としている場合は、既定でコード分析が有効になります。 プロジェクトが .NET Core、.NET Standard、.NET Framework などの別の .NET 実装をターゲットにしている場合は、 [Enablenetanalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティをに設定することによって、手動でコード分析を有効にする必要があり `true` ます。

.NET 5 + SDK に移行しない場合、または NuGet パッケージベースのモデルを使用する場合は、 [Microsoft の CodeAnalysis. Netanalyzers nuget パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)でアナライザーを使用することもできます。 オンデマンドバージョン更新には、パッケージベースのモデルを使用することをお勧めします。

> [!NOTE]
> .NET アナライザーは、ターゲットフレームワークに依存しません。 つまり、プロジェクトは特定の .NET 実装をターゲットにする必要がありません。 アナライザーは、やなど、以前のバージョンの .NET を対象とするプロジェクトでも機能し `net5.0` `netcoreapp3.1` `net472` ます。

ルール違反が analyzer によって検出されると、各ルールの [構成](configuration-options.md)方法に応じて、候補、警告、またはエラーとして報告されます。 コード分析違反は、コンパイラエラーと区別するために "CA" または "IDE" というプレフィックスで示されます。

## <a name="code-quality-analysis"></a>コード品質の分析

*コード品質分析* ("caxxxx") ルールは、セキュリティ、パフォーマンス、設計などの問題について、C# または Visual Basic コードを検査します。 .NET 5.0 以降を対象とするプロジェクトでは、既定で分析が有効になっています。 以前のバージョンの .NET を対象とするプロジェクトでは、 [Enablenetanalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティをに設定することにより、コード分析を有効にすることができ `true` ます。 をに設定することにより、プロジェクトのコード分析を無効にすることもでき `EnableNETAnalyzers` `false` ます。

> [!TIP]
> Visual Studio を使用している場合:
>
> - 多くのアナライザールールには、問題を修正するために適用できる *コード修正プログラム* が関連付けられています。 コード修正は、電球アイコンメニューに表示されます。
> - コード分析を有効または無効にするには、ソリューションエクスプローラーでプロジェクトを右クリックし、[**プロパティ**  >  ] [**コード分析**] タブ > [ **.net アナライザーの有効化**] の順に選択します。

### <a name="enabled-rules"></a>有効なルール

次の規則は、既定では .NET 5.0 で有効になっています。

| 診断 ID | カテゴリ | 重大度 | 説明 |
| - | - | - | - |
| [CA1416](/visualstudio/code-quality/ca1416) | 相互運用性 | 警告 | プラットフォーム互換性アナライザー |
| [CA1417](/visualstudio/code-quality/ca1417) | 相互運用性 | 警告 | `OutAttribute`P/invoke に文字列パラメーターを使用しない |
| [CA1831](/visualstudio/code-quality/ca1831) | パフォーマンス | 警告 | `AsSpan`必要に応じて、範囲ベースのインデクサーの代わりに文字列を使用します。 |
| [CA2013](/visualstudio/code-quality/ca2013) | [信頼性] | 警告 | `ReferenceEquals`値型では使用しない |
| [CA2014](/visualstudio/code-quality/ca2014) | [信頼性] | 警告 | In ループを使用しない `stackalloc` |
| [CA2015](/visualstudio/code-quality/ca2015) | [信頼性] | 警告 | から派生した型にはファイナライザーを定義しないでください。 <xref:System.Buffers.MemoryManager%601> |
| [CA2200](/visualstudio/code-quality/ca2200) | 使用方法 | 警告 | スタック詳細を保持するために再度スローします
| [CA2247](/visualstudio/code-quality/ca2247) | 使用方法 | 警告 | Taskのソースコンストラクターに渡される引数は、ではなく列挙型にする必要があり <xref:System.Threading.Tasks.TaskCreationOptions> ます <xref:System.Threading.Tasks.TaskContinuationOptions> |

これらのルールを無効にするか、エラーに昇格するように、これらのルールの重大度を変更することができます。 [さらに多くのルールを有効に](#enable-additional-rules)することもできます。

- 各 .NET SDK バージョンに含まれる規則の一覧については、「 [Analyzer のリリース](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)」を参照してください。
- すべてのコード品質ルールの一覧については、「 [コード品質ルール](quality-rules/index.md)」を参照してください。

### <a name="enable-additional-rules"></a>追加のルールを有効にする

*分析モード* とは、定義されていないコード分析構成を意味します。この構成では、すべての規則が有効になっていません。 既定の分析モードでは、いくつかのルールのみが [ビルド警告として有効になり](#enabled-rules)ます。 プロジェクトファイルの [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) プロパティを設定することにより、プロジェクトの分析モードを変更できます。 使用できる値は次のとおりです。

| 値 | 説明 |
| - | - |
| `AllDisabledByDefault` | これは最も控えめなモードです。 既定では、すべてのルールが無効になっています。 個々のルールを選択的に[オプトイン](configuration-options.md)して有効にすることができます。<br /><br />`<AnalysisMode>AllDisabledByDefault</AnalysisMode>` |
| `AllEnabledByDefault` | これは最も積極的なモードです。 すべてのルールがビルド警告として有効になります。 個別 [の](configuration-options.md) ルールを選択して無効にすることができます。<br /><br />`<AnalysisMode>AllEnabledByDefault</AnalysisMode>` |
| `Default` | 既定のモードでは、いくつかのルールが警告として有効になっています。その他のルールは、対応するコード修正によって Visual Studio IDE 候補としてのみ有効になり、残りは完全に無効になります。 個々 [の](configuration-options.md) ルールを選択して無効にすることができます。<br /><br />`<AnalysisMode>Default</AnalysisMode>` |

使用可能な各ルールの既定の重要度と、ルールが既定の分析モードで有効になっているかどうかを確認するには、 [ルールの完全な一覧](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)を参照してください。

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

*コードスタイルの分析* ("ide xxxx") 規則を使用すると、コードベースで一貫性のあるコードスタイルを定義および維持できます。 既定の有効化設定は次のとおりです。

- コマンドラインビルド: コマンドラインビルドのすべての .NET プロジェクトに対して、コードスタイルの分析が既定で無効になっています。
- Visual Studio: コードスタイルの分析は、Visual Studio 内のすべての .NET プロジェクトに対して、 [コードリファクタリングのクイックアクション](/visualstudio/ide/code-generation-in-visual-studio)として既定で有効になっています。

.NET 5.0 以降では、コマンドラインと Visual Studio の両方でビルドに対してコードスタイルの分析を有効にすることができます。 コードスタイル違反は、"IDE" プレフィックスが付いた警告またはエラーとして表示されます。 これにより、ビルド時に一貫したコードスタイルを適用できます。

コードスタイルの分析規則の完全な一覧については、「 [コードスタイル規則](style-rules/index.md)」を参照してください。

### <a name="enable-on-build"></a>ビルドで有効にする

ビルドでコードスタイルの分析を有効にするには、次の手順に従います。

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

> [!NOTE]
> コードスタイルの分析機能は試験段階であり、.NET 5 リリースと .NET 6 リリース間で変更される可能性があります。

## <a name="suppress-a-warning"></a>警告の非表示

規則違反を抑制するには、その規則 ID の重大度オプションを `none` EditorConfig ファイルでに設定します。 次に例を示します。

```ini
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio には、コード分析規則からの警告を抑制するための追加の方法が用意されています。 詳細については、「 [違反の抑制](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)」を参照してください。

規則の重大度の詳細については、「 [規則の重要度の構成](configuration-options.md#severity-level)」を参照してください。

## <a name="third-party-analyzers"></a>サード パーティのアナライザー

公式の .NET アナライザーに加えて、 [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [Rosl/ator](https://www.nuget.org/packages/Roslynator.Analyzers/)、 [Xunit](https://www.nuget.org/packages/xunit.analyzers/) [Analyzer、sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)などのサードパーティ製アナライザーをインストールすることもできます。

## <a name="see-also"></a>関連項目

- [コード品質分析ルールのリファレンス](quality-rules/index.md)
- [コードスタイル分析規則のリファレンス](style-rules/index.md)
- [Visual Studio でのコード分析](/visualstudio/code-quality/roslyn-analyzers-overview)
- [.NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md)
- [チュートリアル: 最初のアナライザーとコード修正を作成する](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
