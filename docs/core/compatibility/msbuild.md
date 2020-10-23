---
title: MSBuild に関する破壊的変更
description: MSBuild for .NET Core における破壊的変更の一覧を示します。
ms.date: 02/10/2020
ms.openlocfilehash: 9b0fba30c8955a6099bde0dc95b4df65a151d9e6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159490"
---
# <a name="msbuild-breaking-changes"></a>MSBuild に関する破壊的変更

このページでは、次の破壊的変更について説明します。

| 互換性に影響する変更点 | 導入されたバージョン |
| - | - |
| [TargetFramework が netcoreapp から net に変更される](#targetframework-change-from-netcoreapp-to-net) | 5.0 |
| [.NET 5 を対象とする場合に NETCOREAPP3_1 プリプロセッサ シンボルが定義されない](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | 5.0 |
| [PublishDepsFilePath の動作の変更](#publishdepsfilepath-behavior-change) | 5.0 |
| [Directory.Packages.props ファイルが既定でインポートされる](#directorypackagesprops-files-is-imported-by-default) | 5.0 |
| [リソース マニフェストのファイル名の変更](#resource-manifest-file-name-change) | 3.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [targetframework-name-change](../../../includes/core-changes/msbuild/5.0/targetframework-name-change.md)]

***

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
