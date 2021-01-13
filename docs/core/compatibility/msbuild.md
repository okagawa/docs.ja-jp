---
title: MSBuild に関する破壊的変更
description: MSBuild for .NET Core 3.0 から 3.1 の破壊的変更を一覧で示します。
ms.date: 12/14/2020
ms.openlocfilehash: 1ed5878845406fa7727c644f1e196d63a860646a
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593449"
---
# <a name="msbuild-breaking-changes-in-net-core-30---31"></a>.NET Core 3.0 から 3.1 の MSBuild に関する破壊的変更

このページでは、次の破壊的変更について説明します。

| 互換性に影響する変更点 | 導入されたバージョン |
| - | - |
| [デザイン時のビルドから最上位のパッケージ参照のみが返される](#design-time-builds-only-return-top-level-package-references) | 3.1 |
| [リソース マニフェストのファイル名の変更](#resource-manifest-file-name-change) | 3.0 |

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE [design-time-builds-return-top-level-package-refs](../../../includes/core-changes/msbuild/3.1/design-time-builds-return-top-level-package-refs.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
