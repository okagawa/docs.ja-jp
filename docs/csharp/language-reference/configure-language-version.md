---
title: C# 言語のバージョン管理 - C# ガイド
description: C# 言語のバージョンがプロジェクトに基づいて決定されるしくみとその選択の背後にある理由について説明します。 既定値を手動でオーバーライドする方法について説明します。
ms.date: 05/20/2020
ms.openlocfilehash: bbe5b12e378cf47b7c9b2c8576088e949e526a9a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803006"
---
# <a name="c-language-versioning"></a>C# 言語のバージョン管理

最新の C# コンパイラでは、プロジェクトのターゲット フレームワーク (1 つまたは複数) に基づいて既定の言語バージョンが決定されます。 Visual Studio には値を変更するための UI がありませんが、それは *csproj* ファイルを編集することで変更できます。 既定値を選択すれば、ターゲット フレームワークと互換性がある最新の言語バージョンが使用されます。 プロジェクトのターゲットと互換性がある最新の言語機能にアクセスできるという利点があります。 また、このように既定値を選択すると、ターゲット フレームワークで利用できない型や実行時動作を必要とする言語が使用されません。 既定値より新しい言語バージョンを選択すると、コンパイル時間や実行時エラーの診断が困難になることがあります。

この記事の規則は、Visual Studio 2019 または .NET Core 3.0 SDK に付属するコンパイラに適用されます。 Visual Studio 2017 インストールまたは以前の .NET Core SDK バージョンに含まれる C# コンパイラは、既定で C# 7.0 を対象とします。

C# 8.0 (以降) は .NET Core 3.x 以降のバージョンでのみサポートされています。 最新機能の多くには、.NET Core 3.x で導入されたライブラリとランタイムの機能が必要になります。

- [既定のインターフェイスの実装](../whats-new/csharp-8.md#default-interface-methods)では、.NET Core 3.0 CLR の新機能が必要です。
- [非同期ストリーム](../whats-new/csharp-8.md#asynchronous-streams)には、新しい型 <xref:System.IAsyncDisposable?displayProperty=nameWithType>、<xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>、<xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> が必要です。
- [インデックスと範囲](../whats-new/csharp-8.md#indices-and-ranges)には、新しい型 <xref:System.Index?displayProperty=nameWithType> と <xref:System.Range?displayProperty=nameWithType> が必要です。
- [null 許容参照型](../whats-new/csharp-8.md#nullable-reference-types)では、より適切な警告を提供するためにいくつかの[属性](attributes/nullable-analysis.md)が利用されます。 その属性は .NET Core 3.0 で追加されました。 他のターゲット フレームには、そのような属性に関する注釈が付けられていません。 つまり、null 許容警告は潜在的な問題を正確に反映していない可能性があります。

## <a name="defaults"></a>[既定値]

コンパイラでは、以下の規則に基づいて既定値が決定されます。

| ターゲット フレーム | version | C# 言語の既定のバージョン |
|------------------|---------|-----------------------------|
| .NET Core        | 3.x     | C# 8.0                      |
| .NET Core        | 2.x     | C# 7.3                      |
| .NET Standard    | 2.1     | C# 8.0                      |
| .NET Standard    | 2.0     | C# 7.3                      |
| .NET Standard    | 1.x     | C# 7.3                      |
| .NET Framework   | all     | C# 7.3                      |

ご自分のプロジェクトが、対応するプレビュー バージョンの言語を持つプレビュー フレームワークをターゲットにしている場合、使用される言語バージョンはプレビュー バージョンの言語です。 環境を問わず、そのプレビューでは最新の機能が使用されます。リリース済みの .NET Core バージョンをターゲットにするプロジェクトに影響はありません。

## <a name="override-a-default"></a>既定値のオーバーライド

C# のバージョンを明示的に指定する必要がある場合は、いくつかの方法で実行できます。

- [プロジェクト ファイル](#edit-the-project-file)を手動で編集する。
- [サブディレクトリ内の複数のプロジェクトに対して](#configure-multiple-projects)言語バージョンを設定する。
- [`-langversion` コンパイラ オプション](compiler-options/langversion-compiler-option.md)を構成する。

### <a name="edit-the-project-file"></a>プロジェクト ファイルを編集する

プロジェクト ファイルで言語のバージョンを設定できます。 たとえば、プレビュー機能に明示的にアクセスしたい場合は、次のように要素を追加します。

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

値 `preview` では、コンパイラでサポートされている使用可能な最新のプレビュー C# 言語バージョンが使用されます。

### <a name="configure-multiple-projects"></a>複数のプロジェクトを構成する

複数のプロジェクトを構成するには、`<LangVersion>` 要素を含む **Directory.build.props** ファイルを作成します。 この操作は通常、ソリューション ディレクトリで実行します。 ソリューション ディレクトリ内の **Directory.Build.props** ファイルに以下を追加します。

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

そのファイルが含まれるディレクトリのすべてのサブディレクトリ内のビルドで、プレビュー C# バージョンが使用されます。 詳しくは、「[ビルドのカスタマイズ](/visualstudio/msbuild/customize-your-build)」を参照してください。

## <a name="c-language-version-reference"></a>C# 言語バージョン リファレンス

次の表では、現在のすべての C# 言語バージョンを示します。 コンパイラが古い場合、一部の値が正しく解釈されない可能性があります。 .NET Core 3.0 以降をインストールすれば、一覧にあるすべてにアクセスできます。

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> お使いのコンピューターで使用可能な言語バージョンの一覧を表示するには、[Visual Studio の開発者コマンド プロンプト](../../framework/tools/developer-command-prompt-for-vs.md)を開き、次のコマンドを実行します。
>
> ```CMD
> csc -langversion:?
> ```
>
> このように [-langversion](compiler-options/langversion-compiler-option.md) コンパイル オプションを指定すると、次のような内容が出力されます。
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
