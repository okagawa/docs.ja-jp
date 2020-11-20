---
title: dotnet tool search コマンド
description: dotnet tool search コマンドは、NuGet.org に発行されている .NET ツールを検索します。
ms.date: 11/11/2020
ms.openlocfilehash: e0289e651ec4a439c791c8c948bef2d85d9c3794
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634143"
---
# <a name="dotnet-tool-search"></a>dotnet tool search

**この記事の対象:**  ✔️ .NET 5.0 SDK 以降のバージョン

## <a name="name"></a>名前

`dotnet tool search` - NuGet に発行されているすべての [.NET ツール](global-tools.md)を検索します。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet tool search [--detail]  [--prerelease]
    [--skip <NUMBER>] [--take <NUMBER>] <SEARCH TERM>

dotnet tool search -h|--help
```

## <a name="description"></a>説明

`dotnet tool search` コマンドを使用すると、NuGet で .NET のグローバル、ツールパス、またはローカル ツールとして使用できるツールを検索することができます。 このコマンドは、ツールの名前とメタデータ (タイトル、説明、タグなど) を検索します。

このコマンドでは、[NuGet Search API](/nuget/api/search-query-service-resource#search-for-packages) を使用します。 これにより `packageType=dotnettool` がフィルター処理され、.NET ツール パッケージのみが選択されます。

## <a name="options"></a>Options

- **`--detail`**

  クエリの詳細な結果を表示します。

- **`--prerelease`**

  プレリリース パッケージを含めます。

- **`--skip <NUMBER>`**

  スキップするクエリ結果の数を指定します。 改ページ位置の自動修正に使用されます。

- **`--take <NUMBER>`**

  表示するクエリ結果の数を指定します。 改ページ位置の自動修正に使用されます。

- **`-h|--help`**

  コマンド ライン ヘルプを表示します。

## <a name="examples"></a>例

- NuGet.org でパッケージ名または説明に "format" が含まれている .NET ツールを検索します。

  ```dotnetcli
  dotnet tool search format
  ```

  出力は次の例のようになります。

  ```output
  Package ID                              Latest Version      Authors                                                                     Downloads      Verified
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------
  dotnet-format                           4.1.131201          Microsoft                                                                   496746
  bsoa.generator                          1.0.0               Microsoft                                                                   533
  ```

- NuGet.org でパッケージ名またはメタデータに "format" が含まれている .NET ツールを検索し、最初の結果のみを表示して、詳細ビューを表示します。

  ```dotnetcli
  dotnet tool search format --take 1 --detail
  ```

  出力は次の例のようになります。

  ```output
  ----------------
  dotnet-format
  Latest Version: 4.1.131201
  Authors: Microsoft
  Tags:
  Downloads: 496746
  Verified: False
  Description: Command line tool for formatting C# and Visual Basic code files based on .editorconfig settings.
  Versions:
          3.0.2 Downloads: 1973
          3.0.4 Downloads: 9064
          3.1.37601 Downloads: 114730
          3.2.107702 Downloads: 13423
          3.3.111304 Downloads: 131195
          4.0.130203 Downloads: 78610
          4.1.131201 Downloads: 145927
  ```

## <a name="see-also"></a>関連項目

- [.NET ツール](global-tools.md)
- [チュートリアル: .NET CLI を使って .NET グローバル ツールをインストールして使用する](global-tools-how-to-use.md)
- [チュートリアル: .NET CLI を使って .NET ローカル ツールをインストールして使用する](local-tools-how-to-use.md)
