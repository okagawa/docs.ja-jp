---
title: 単一ファイル アプリケーション
description: 単一ファイル アプリケーションの概要、およびこのアプリケーション デプロイ モデルの使用を検討すべき理由について説明します。
author: lakshanf
ms.author: lakshanf
ms.date: 12/17/2020
ms.openlocfilehash: fb768fa6fe390fbe8390e441f4eb71c3172ad395
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505427"
---
# <a name="single-file-deployment-and-executable"></a>単一ファイルの配置と実行可能ファイル

アプリケーションに依存するすべてのファイルを単一のバイナリにバンドルすることで、アプリケーション開発者は、アプリケーションを単一ファイルとして配置し、配布することができます。 このデプロイ モデルは、.NET Core 3.0 以降で利用可能であり、.NET 5.0 で拡張されています。 以前の .NET Core 3.0 では、ユーザーが単一ファイル アプリを実行する場合、そのアプリケーションが実行される前に、まず .NET Core ホストがすべてのファイルを一時ディレクトリに抽出します。 .NET 5.0 では、アプリからファイルを抽出する必要がなく、コードを直接実行するので、このエクスペリエンスが向上しています。

[フレームワークに依存するデプロイ モデル](index.md#publish-framework-dependent)と[自己完結型アプリケーション](index.md#publish-self-contained)の両方で、単一ファイルの配置が可能です。 自己完結型アプリケーション内にある単一ファイルは、ランタイム ライブラリとフレームワーク ライブラリが含まれるため、大きなサイズとなります。 単一ファイル配置オプションは、[ReadyToRun](ready-to-run.md) と [Trim (.NET 5.0 の試験的な機能)](trim-self-contained.md) の各発行オプションと組み合わせることができます。

## <a name="api-incompatibility"></a>API の非互換性

一部の API は、単一ファイルの配置と互換性がありません。また、これらの API を使用する場合、アプリケーションで変更が必要になることがあります。 サードパーティのフレームワークまたはパッケージを使用する場合、それらでこれらの API のいずれかが使用されていて、変更が必要になる可能性があります。 問題の最も一般的な原因は、アプリケーションに付属するファイルまたは DLL のファイル パスに依存していることです。

次の表では、単一ファイルの使用に関連するランタイム ライブラリ API の詳細を示します。

| API                            | Note                                                                   |
|--------------------------------|------------------------------------------------------------------------|
| `Assembly.Location`            | 空の文字列を返します。                                               |
| `Module.FullyQualifiedName`    | 値が `<Unknown>` である文字列が返されるか、例外がスローされます。 |
| `Module.Name`                  | 値が `<Unknown>` である文字列が返されます。                        |
| `Assembly.GetFile`             | <xref:System.IO.IOException> をスローします。                                   |
| `Assembly.GetFiles`            | <xref:System.IO.IOException> をスローします。                                   |
| `Assembly.CodeBase`            | <xref:System.PlatformNotSupportedException> をスローします。                    |
| `Assembly.EscapedCodeBase`     | <xref:System.PlatformNotSupportedException> をスローします。                    |
| `AssemblyName.CodeBase`        | `null` を返します。                                                        |
| `AssemblyName.EscapedCodeBase` | `null` を返します。                                                        |

一般的なシナリオを修正するための推奨事項がいくつかあります。

* 実行可能ファイルの隣にあるファイルにアクセスするには、<xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> を使用します。

* 実行可能ファイルのファイル名を検索するには、<xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType> の最初の要素を使用します。

* Loose ファイルが完全に配布されないようにするには、[埋め込みリソース](../../framework/resources/creating-resource-files-for-desktop-apps.md)を使用することを検討します。

## <a name="attaching-a-debugger"></a>デバッガーのアタッチ

Linux では、自己完結型の単一ファイル プロセスにアタッチしたり、クラッシュ ダンプをデバッグしたりできる唯一のデバッガーは、[LLDB を使用する SOS](../diagnostics/dotnet-sos.md) です。

Windows と Mac では、Visual Studio と VS Code を使用してクラッシュ ダンプをデバッグできます。 実行中の自己完結型単一ファイルの実行可能ファイルにアタッチするには、余分なファイル _mscordbi.{dll,so}_ が必要です。

このファイルがないと、Visual Studio で次のエラーが発生することがあります: "プロセスにアタッチできません。 デバッグ コンポーネントはインストールされていません。" また、VS Code では、次のエラーが発生することがあります: "プロセスにアタッチできませんでした: 不明なエラー: 0x80131c3c。"

これらのエラーを修正するには、実行可能ファイルの隣に _mscordbi_ をコピーする必要があります。 _mscordbi_ は、既定では、アプリケーションのランタイム ID でサブディレクトリに `publish` されます。 そのため、たとえば、`dotnet` CLI と `-r win-x64` パラメーターを使用して Windows 用に自己完結型単一ファイルの実行可能ファイルを発行する場合、実行可能ファイルは _bin/Debug/net5.0/win-x64/publish_ に配置されます。 _mscordbi.dll_ のコピーは _bin/Debug/net5.0/win-x64_ にあります。

## <a name="other-considerations"></a>その他の考慮事項

既定では、単一ファイルを使用してネイティブ ライブラリをバンドルすることができません。 Linux では、ランタイム ライブラリをバンドルに事前にリンクして、アプリケーション ネイティブ ライブラリのみを単一ファイル アプリと同じディレクトリに配置します。 Windows では、ホスト コードのみを事前にリンクして、ランタイム ライブラリとアプリケーション ネイティブ ライブラリの両方を単一ファイル アプリと同じディレクトリに配置します。 これにより、優れたデバッグ エクスペリエンスが確保されます。それには、ネイティブ ファイルを単一ファイルから除外する必要があります。 単一ファイル バンドルにネイティブ ライブラリを含めるようにフラグ `IncludeNativeLibrariesForSelfExtract` を設定するオプションがありますが、これらのファイルは、単一ファイル アプリケーションが実行されるときに、クライアント コンピューターの一時ディレクトリに抽出されます。

`IncludeAllContentForSelfExtract` を指定すると、実行可能ファイルを実行する前にすべてのファイルが抽出されます。 これにより、元の .NET Core の単一ファイル展開動作が保持されます。

単一ファイル アプリケーションでは、関連するすべての PDB ファイルは隣に配置され、既定ではバンドルされません。 ビルドするプロジェクトのアセンブリ内に PDB を含めるには、[以下](#include-pdb-files-inside-the-bundle)で詳しく説明するように、`DebugType` を `embedded` に設定します。

マネージド C++ コンポーネントは、単一ファイルの配置には適していません。単一ファイルとの互換性を確保するには、アプリケーションを C# または別の非マネージド C++ 言語で記述することをお勧めします。

## <a name="exclude-files-from-being-embedded"></a>ファイルを埋め込み対象から除外する

次のメタデータを設定すると、特定のファイルを単一ファイルの埋め込み対象から明示的に除外することができます。

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

たとえば、いくつかのファイルを発行ディレクトリに配置するものの、単一ファイルへのバンドルは行わない場合などです。

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="include-pdb-files-inside-the-bundle"></a>バンドル内に PDB ファイルを含める

アセンブリの PDB ファイルは、次の設定を使用して、アセンブリ自体 (`.dll`) に埋め込むことができます。 シンボルはアセンブリの一部であるため、単一ファイル アプリケーションの一部にもなります。

```xml
<DebugType>embedded</DebugType>
```

たとえば、アセンブリに PDB ファイルを埋め込むには、そのアセンブリのプロジェクト ファイルに次のプロパティを追加します。

```xml
<PropertyGroup>
  <DebugType>embedded</DebugType>
</PropertyGroup>
```

## <a name="publish-a-single-file-app---sample-project-file"></a>単一のファイル アプリを発行する - サンプル プロジェクト ファイル

単一ファイルの発行を指定するサンプル プロジェクト ファイルを次に示します。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <PublishSingleFile>true</PublishSingleFile>
    <SelfContained>true</SelfContained>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <PublishReadyToRun>true</PublishReadyToRun>
  </PropertyGroup>

</Project>
```

これらのプロパティには、次の関数があります。

* `PublishSingleFile` - 単一ファイルの発行を有効にします。
* `SelfContained` - アプリが自己完結型またはフレームワーク依存であるかを判断します。
* `RuntimeIdentifier` - ターゲットとする [OS と CPU の種類](../rid-catalog.md)を指定します。
* `PublishTrimmed` - 自己完結型アプリでのみサポートされている[アセンブリのトリミング](trim-self-contained.md)の使用を有効にします。
* `PublishReadyToRun` - [Ahead-Of-Time (AOT) コンパイル](ready-to-run.md)を有効にします。

**注:**

* アプリは OS とアーキテクチャに固有のものです。 Linux x64、Linux ARM64、Windows x64 など、構成ごとに発行する必要があります。
* 構成ファイル ( *\*.runtimeconfig.json* など) は、単一ファイルに含まれています。 追加の構成ファイルが必要な場合は、その単一ファイルの横に配置することができます。

## <a name="publish-a-single-file-app---cli"></a>単一ファイル アプリを発行する - CLI

[dotnet publish](../tools/dotnet-publish.md) コマンドを使用して、単一ファイル アプリケーションを発行します。 アプリを発行する場合、次のプロパティを設定します。

- 特定のランタイムに対して発行する: `-r win-x64`
- 単一ファイルとして発行する: `-p:PublishSingleFile=true`

次の例では、Windows 用のアプリを自己完結型の単一ファイル アプリケーションとして発行します。

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

次の例では、Linux 用のアプリをフレームワークに依存する単一ファイル アプリケーションとして発行します。

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

詳細については、「[.NET Core CLI を使用して .NET Core アプリを発行する](deploy-with-cli.md)」を参照してください。

## <a name="publish-a-single-file-app---visual-studio"></a>単一ファイル アプリを発行する - Visual Studio

Visual Studio を使用すると、アプリケーションの発行方法を制御する再利用可能な発行プロファイルを作成できます。

01. **[ソリューション エクスプローラー]** ペインで、発行するプロジェクトを右クリックします。 **[発行]** を選択します。

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="右クリック メニューの [発行] オプションが強調表示されたソリューション エクスプローラー。":::

    発行プロファイルがまだない場合は、指示に従って作成し、ターゲットの種類として **[フォルダー]** を選択します。

01. **[編集]** を選択します。

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Visual Studio の発行プロファイルと [編集] ボタン":::

01. **[プロファイル設定]** ダイアログで、次のオプションを設定します。

    - **[配置モード]** を **[自己完結]** または **[フレームワーク依存]** に設定します。
    - **[ターゲット ランタイム]** を発行先のプラットフォームに設定します。 ( **[移植可能]** 以外にする必要があります)。
    - **[単一ファイルの作成]** を選択します。

    **[保存]** を選択して設定を保存し、 **[発行]** ダイアログに戻ります。

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="[配置モード]、[ターゲット ランタイム]、[単一ファイルの作成] の各オプションが強調表示されている [プロファイル設定] ダイアログ。":::

01. **[発行]** を選択して、アプリを単一ファイルとして発行します。

詳細については、[Visual Studio を使用した .NET Core アプリの発行](deploy-with-vs.md)に関するページを参照してください。

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a>単一ファイル アプリを発行する - Visual Studio for Mac

Visual Studio for Mac には、アプリを単一ファイルとして発行するためのオプションがありません。 「[単一ファイル アプリを発行する - CLI](#publish-a-single-file-app---cli)」セクションの手順に従って、手動で発行する必要があります。 詳細については、「[.NET Core CLI を使用して .NET Core アプリを発行する](deploy-with-cli.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [.NET Core アプリケーションの配置](index.md)。
- [.NET Core CLI を使用して .NET Core アプリを発行する](deploy-with-cli.md)。
- [Visual Studio を使用して .NET Core アプリを発行する](deploy-with-vs.md)。
- [`dotnet publish` コマンド](../tools/dotnet-publish.md)。
