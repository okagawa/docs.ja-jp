---
title: 破壊的変更:Directory.Packages.props ファイルが既定でインポートされる
description: .NET 5.0 での破壊的変更について学習します。Directory.Packages.props という名前のファイルがプロジェクト フォルダーに含まれている場合、NuGet の .props ファイルによってそのファイルのインポートが自動的に行われます。
ms.date: 09/17/2020
ms.openlocfilehash: ee8a2999b801e81750d96a0bc985e3c8169224a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759407"
---
# <a name="directorypackagesprops-files-is-imported-by-default"></a>Directory.Packages.props ファイルが既定でインポートされる

NuGet の *.props* ファイルでは、*Directory.Packages.props* という名前のファイルがプロジェクト フォルダーまたはその先祖に含まれている場合は、そのファイルのインポートが自動的に行われます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="change-description"></a>変更の説明

以前の .NET バージョンでは、*Directory.Packages.props* という名前のファイルをプロジェクト ファイルに含めることができ、ビルド時に NuGet の *.props* によって自動的にインポートされることはありませんでした。

.NET 5.0 以降では、このようなファイルがプロジェクト フォルダーまたはその先祖に存在している場合は、そのファイルのインポートが自動的に "*行われます*"。 この名前のファイルがプロジェクト フォルダーにある場合は、この自動インポート機能によってビルドの動作が変わる可能性があります。 たとえば、そのファイルは今後インポートされるものの以前はインポートされていなかったか、明示的にインポートした場合にインポートされる順序が変わるなどします。

## <a name="reason-for-change"></a>変更理由

この変更は、NuGet を対象とした[パッケージのバージョン集中管理](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions)をサポートするために行われました。

## <a name="recommended-action"></a>推奨アクション

既存の *Directory.Packages.props* ファイルが自動的にインポートされないようにする場合は、そのファイルの名前を変更します。

## <a name="affected-apis"></a>影響を受ける API

N/A

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
