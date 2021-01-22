---
title: AssemblyInfo プロパティ
description: アセンブリ属性と、それらが .NET Core 2.1 以降のバージョンでの MSBuild プロパティとどのように対応するかについて説明します。
ms.topic: reference
ms.date: 01/08/2021
ms.openlocfilehash: a2c431b3fe3da428f21582624ca5f357887e2815
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192874"
---
# <a name="map-assemblyinfo-attributes-to-properties"></a>AssemblyInfo 属性をプロパティにマップする

.NET Core 2.0 以前のバージョンにおいて *AssemblyInfo* ファイルに通常存在していた[アセンブリ属性](../../standard/assembly/set-attributes.md)は、.NET Core 2.1 以降では、MSBuild プロパティから自動的に生成されます。

## <a name="properties-per-attribute"></a>属性ごとのプロパティ

次の表に示すように、各属性にはその内容を制御する対応するプロパティと、その生成を無効にする別のものがあります。

| 属性                                                      | プロパティ               | 無効にするプロパティ                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

メモ:

- `AssemblyVersion` と `FileVersion` の既定値は、サフィックスのない `$(Version)` の値です。 たとえば、`$(Version)` が `1.2.3-beta.4` の場合、値は `1.2.3` です。
- `InformationalVersion` の既定値は、`$(Version)` の値です。
- `$(SourceRevisionId)` プロパティが存在する場合は、それが `InformationalVersion` の後に追加されます。 `IncludeSourceRevisionInInformationalVersion` を使用して、この動作を無効にすることができます。
- NuGet メタデータには、`Copyright` および `Description` プロパティも使用されます。
- `Configuration` (既定値は `Debug`) は、すべての MSBuild ターゲットと共有されます。 これは、`dotnet` コマンド ([dotnet pack](../tools/dotnet-pack.md) など) の `--configuration` オプションを使用して設定できます。

## <a name="generateassemblyinfo"></a>GenerateAssemblyInfo

AssemblyInfo の生成を有効または無効にするブール値。 既定値は `true` です。

## <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

生成されるアセンブリ情報ファイルの相対パスまたは絶対パス。 既定値は、`$(IntermediateOutputPath)` (*obj*) ディレクトリ内の *[プロジェクト名].AssemblyInfo.[cs|vb]* という名前のファイルです。
