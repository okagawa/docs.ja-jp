---
title: Microsoft.NET.Sdk.Desktop の MSBuild プロパティ
description: .NET デスクトップ SDK によって認識される MSBuild のプロパティと項目のリファレンス (WPF と WinForms を含む)。
ms.date: 02/04/2021
ms.topic: reference
author: adegeo
ms.author: adegeo
ms.custom: updateeachrelease
no-loc:
- App.xaml
- Application.xaml
- ApplicationDefinition
- Page
- EmbeddedResource
- Compile
- None
ms.openlocfilehash: 6d1903558dd03776a72eb6ee56ddae09fb66615b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488249"
---
# <a name="msbuild-reference-for-net-desktop-sdk-projects"></a>.NET デスクトップ SDK プロジェクトの MSBuild リファレンス

このページは、.NET デスクトップ SDK で Windows フォーム (WinForms) および Windows Presentation Foundation (WPF) プロジェクトを構成するために使用する MSBuild のプロパティと項目についてのリファレンスです。

> [!NOTE]
> この記事では、デスクトップ アプリに関連する .NET SDK の MSBuild プロパティのサブセットについて説明します。 .NET SDK 固有の一般的な MSBuild プロパティの一覧については、「[.NET SDK プロジェクトの MSBuild リファレンス](msbuild-props.md)」を参照してください。 一般的な MSBuild プロパティの一覧については、「[MSBuild プロジェクトの共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)」を参照してください。

## <a name="enable-net-desktop-sdk"></a>.NET デスクトップ SDK を有効にする

WinForms または WPF を使用するには、プロジェクト ファイルを構成します。

### <a name="net-50"></a>.NET 5.0

WinForms または WPF プロジェクトのプロジェクト ファイルで、次の設定を指定します。

- .NET SDK `Microsoft.NET.Sdk` をターゲットとする。 詳細については、「[プロジェクト ファイル](overview.md#project-files)」を参照してください。
- [`TargetFramework`](msbuild-props.md#targetframework) を `net5.0-windows` に設定する。
- UI フレームワーク プロパティを 1 つ (または、必要に応じて両方) を追加する。
  - WPF をインポートして使用する場合は、[`UseWPF`](#usewpf) を `true` に設定する。
  - WinForms をインポートして使用する場合は、[`UseWindowsForms`](#usewindowsforms) を `true` に設定する。
- (省略可能) `OutputType` を `WinExe` に設定する。 これにより、ライブラリではなく、アプリが生成されます。 ライブラリを生成する場合は、このプロパティを省略してください。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>

    <UseWPF>true</UseWPF>
    <!-- and/or -->
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

### <a name="net-core-31"></a>.NET Core 3.1

WinForms または WPF プロジェクトのプロジェクト ファイルで、次の設定を指定します。

- .NET SDK `Microsoft.NET.Sdk.WindowsDesktop` をターゲットとする。 詳細については、「[プロジェクト ファイル](overview.md#project-files)」を参照してください。
- [`TargetFramework`](msbuild-props.md#targetframework) を `netcoreapp3.1` に設定する。
- UI フレームワーク プロパティを 1 つ (または、必要に応じて両方) を追加する。
  - WPF をインポートして使用する場合は、[`UseWPF`](#usewpf) を `true` に設定する。
  - WinForms をインポートして使用する場合は、[`UseWindowsForms`](#usewindowsforms) を `true` に設定する。
- (省略可能) `OutputType` を `WinExe` に設定する。 これにより、ライブラリではなく、アプリが生成されます。 ライブラリを生成する場合は、このプロパティを省略してください。

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>

    <UseWPF>true</UseWPF>
    <!-- and/or -->
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

## <a name="wpf-default-includes-and-excludes"></a>WPF に既定で含まれるものと除外されるもの

SDK プロジェクトでは、プロジェクトからファイルを暗黙的に含めるまたは除外する規則のセットを定義します。 これらの規則により、ファイルのビルド アクションも自動的に設定されます。 これは、既定で含めるまたは除外する規則がない古い SDK 以外の .NET Framework プロジェクトとは異なります。 .NET Framework プロジェクトでは、プロジェクトに含めるファイルを明示的に宣言する必要があります。

.NET プロジェクト ファイルには、ファイルを自動的に処理するための[規則の標準セット](overview.md#default-includes-and-excludes)が含まれています。 WPF プロジェクトではさらに規則を追加します。

次の表には、[`UseWPF`](#usewpf) プロジェクト プロパティが `true` に設定されている場合に、.NET デスクトップ SDK に含まれる、および除外される要素と [glob](https://en.wikipedia.org/wiki/Glob_(programming)) が示されています。

| 要素               | 含まれる glob                 | 除外される glob                                                                                           | glob の削除  |
|-----------------------|------------------------------|--------------------------------------------------------------------|--------------|
| ApplicationDefinition | App.xaml または Application.xaml | 該当なし                                                                | 該当なし          |
| Page                  | \*\*/\*.xaml                 | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc<br>*ApplicationDefinition* によって定義されたすべての XAML | 該当なし          |
| None                  | 該当なし                          | 該当なし                                                                | \*\*/\*.xaml |

以下は、すべてのプロジェクトの種類について、既定で含まれるものと除外されるものの設定です。 詳細については、「[既定で含まれるものと除外されるもの](overview.md#default-includes-and-excludes)」を参照してください。

| 要素           | 含まれる glob                              | 除外される glob                                                  | glob の削除              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compile           | \*\*/\*.cs; \*\*/\*.vb (またはその他の言語拡張) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | N/A          |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | N/A                      |
| None              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs; \*\*/\*.resx |

### <a name="errors-related-to-duplicate-items"></a>"重複する" 項目に関するエラー

ファイルをプロジェクトに明示的に追加した場合、またはプロジェクトにファイルを自動的に含めるように XAML glob が設定されている場合は、次のいずれかのエラーが発生する可能性があります。

* 重複する 'ApplicationDefinition' 項目が含まれていました。
* 重複する 'Page' 項目が含まれていました。

これらのエラーは、ご自分の設定と競合する暗黙的な "*含まれる*" glob の結果です。 この問題を回避するには、[`EnableDefaultApplicationDefinition`](#enabledefaultapplicationdefinition) または [`EnableDefaultPageItems`](#enabledefaultpageitems) を `false` に設定します。 これらの値を `false` に設定すると、プロジェクトで既定の glob を明示的に定義するか、プロジェクトに含めるファイルを明示的に定義する必要があった以前の SDK の動作に戻ります。

[`EnableDefaultItems` プロパティ](msbuild-props.md#enabledefaultitems)を `false` に設定することにより、暗黙的な含まれるものを完全に無効にすることができます。

## <a name="wpf-settings"></a>WPF の設定

- [UseWPF](#usewpf)
- [EnableDefaultApplicationDefinition](#enabledefaultapplicationdefinition)
- [EnableDefaultPageItems](#enabledefaultpageitems)

WPF 固有ではないプロジェクト設定については、「[.NET SDK プロジェクトの MSBuild リファレンス](msbuild-props.md)」を参照してください。

### <a name="usewpf"></a>UseWPF

`UseWPF` プロパティにより、WPF ライブラリへの参照を含めるかどうかが制御されます。 また、これにより、WPF プロジェクトと関連ファイルを正しく処理するために MSBuild パイプラインが変更されます。 既定値は `false` です。 `UseWPF` プロパティを `true` に設定して、WPF のサポートを有効にします。 このプロパティが有効になっている場合にのみ、Windows プラットフォームをターゲットにすることができます。

```xml
<PropertyGroup>
  <UseWPF>true</UseWPF>
</PropertyGroup>
```

このプロパティが `true` に設定されている場合は、.NET 5.0 以降のプロジェクトで [.NET デスクトップ SDK](#enable-net-desktop-sdk) が自動的にインポートされます。

.NET Core 3.1 のプロジェクトの場合、このプロパティを使用するには [.NET デスクトップ SDK](#enable-net-desktop-sdk) を明示的にターゲットとする必要があります。

### <a name="enabledefaultapplicationdefinition"></a>EnableDefaultApplicationDefinition

`EnableDefaultApplicationDefinition` プロパティにより、`ApplicationDefinition` 項目がプロジェクトに暗黙的に含まれるかどうかが制御されます。 既定値は `true` です。 `EnableDefaultApplicationDefinition` プロパティを `false` に設定して、暗黙的なファイルの組み込みを無効にします。

```xml
<PropertyGroup>
  <EnableDefaultApplicationDefinition>false</EnableDefaultApplicationDefinition>
</PropertyGroup>
```

このプロパティを使用するには、[`EnableDefaultItems` プロパティ](msbuild-props.md#enabledefaultitems)が `true` に設定されている (既定の設定) 必要があります。

### <a name="enabledefaultpageitems"></a>EnableDefaultPageItems

`EnableDefaultPageItems` プロパティにより、 _.xaml_ ファイルである `Page` 項目がプロジェクトに暗黙的に含まれるかどうかが制御されます。 既定値は `true` です。 `EnableDefaultPageItems` プロパティを `false` に設定して、暗黙的なファイルの組み込みを無効にします。

```xml
<PropertyGroup>
  <EnableDefaultPageItems>false</EnableDefaultPageItems>
</PropertyGroup>
```

このプロパティを使用するには、[`EnableDefaultItems` プロパティ](msbuild-props.md#enabledefaultitems)が `true` に設定されている (既定の設定) 必要があります。

## <a name="windows-forms-settings"></a>Windows フォームの設定

- [UseWindowsForms](#usewindowsforms)

WinForms 固有ではないプロジェクト プロパティについては、「[.NET SDK プロジェクトの MSBuild リファレンス](msbuild-props.md)」を参照してください。

### <a name="usewindowsforms"></a>UseWindowsForms

`UseWindowsForms` プロパティにより、Windows フォームをターゲットとするようにアプリケーションがビルドされるかどうかが制御されます。 このプロパティにより、Windows フォーム プロジェクトと関連ファイルを正しく処理するために MSBuild パイプラインが変更されます。 既定値は `false` です。 `UseWindowsForms` プロパティを `true` に設定して、Windows フォームのサポートを有効にします。 この設定が有効になっている場合にのみ、Windows プラットフォームをターゲットにすることができます。

```xml
<PropertyGroup>
  <UseWindowsForms>true</UseWindowsForms>
</PropertyGroup>
```

このプロパティが `true` に設定されている場合は、.NET 5.0 以降のプロジェクトで [.NET デスクトップ SDK](#enable-net-desktop-sdk) が自動的にインポートされます。

.NET Core 3.1 のプロジェクトの場合、このプロパティを使用するには [.NET デスクトップ SDK](#enable-net-desktop-sdk) を明示的にターゲットとする必要があります。

## <a name="shared-settings"></a>共有設定

- [DisableWinExeOutputInference](#disablewinexeoutputinference)

### <a name="disablewinexeoutputinference"></a>DisableWinExeOutputInference

.NET 5.0 SDK 以降に適用されます。

アプリで `OutputType` プロパティに対して `Exe` 値が設定されているときに、そのアプリがコンソールから実行されていない場合はコンソール ウィンドウが作成されます。 これは通常、Windows デスクトップ アプリの望ましい動作ではありません。 `WinExe` 値を使用すると、コンソール ウィンドウは作成されません。 .NET 5.0 SDK 以降では、`Exe` 値が `WinExe` に自動的に変換されます。

`DisableWinExeOutputInference` プロパティは、`Exe` を `WinExe` として扱う動作を元に戻します。 この値を `true` に設定して、`Exe` の `OutputType` プロパティ値の動作を復元します。 既定値は `false` です。

```xml
<PropertyGroup>
  <DisableWinExeOutputInference>true</DisableWinExeOutputInference>
</PropertyGroup>
```

## <a name="see-also"></a>関連項目

- [.NET プロジェクト SDK](overview.md)
- [.NET SDK プロジェクトの MSBuild リファレンス](msbuild-props.md)
- [MSBuild スキーマ リファレンス](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [MSBuild の共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)
- [ビルドのカスタマイズ](/visualstudio/msbuild/customize-your-build)
