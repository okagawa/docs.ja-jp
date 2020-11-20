---
title: dotnet tool list コマンド
description: dotnet tool list コマンドを実行すると、お使いのコンピューターにインストールされている .NET ツールが一覧表示されます。
ms.date: 02/14/2020
ms.openlocfilehash: d884f2c41834dd9704de3a8ca15417ba368fde4b
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634286"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン

## <a name="name"></a>名前

`dotnet tool list` - お使いのコンピューターに現在インストールされている指定した種類の [.NET ツール](global-tools.md)を一覧表示します。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a>説明

`dotnet tool list` コマンドを実行すると、お使いのコンピューターにインストールされている .NET グローバル ツール、ツールパス、またはローカル ツールが一覧表示されます。 コマンドでは、パッケージ名、インストールされているバージョン、およびツール コマンドを一覧表示します。  コマンドを使用するには、次のいずれかを指定します。

* 既定の場所にインストールされているグローバル ツールを一覧表示するには、`--global` オプションを使用します。
* ユーザー指定の場所にインストールされているグローバル ツールを一覧表示するには、`--tool-path` オプションを使用します。
* ローカル ツールを一覧表示するには、`--local` オプションを使用するか、`--global` オプション、`--tool-path` オプション、および `--local` オプションを省略します。

**ローカル ツールは .NET Core SDK 3.0 以降で使用できます。**

## <a name="options"></a>オプション

- **`-g|--global`**

  ユーザー全体のグローバル ツールを一覧表示します。 `--tool-path` オプションと組み合わせることはできません。 `--global` と `--tool-path` の両方を省略すると、ローカル ツールが一覧表示されます。

- **`-h|--help`**

  コマンドの短いヘルプを印刷します。

- **`--local`**

  現在のディレクトリのローカル ツールを一覧表示します。 `--global` または `--tool-path` オプションとは組み合わせることはできません。 `--global` と `--tool-path` の両方を省略すると、`--local` が指定されていない場合でも、ローカル ツールが一覧表示されます。

- **`--tool-path <PATH>`**

  グローバル ツールを検索するカスタムの場所を指定します。 PATH は絶対パスでも相対パスでもかまいません。 `--global` オプションと組み合わせることはできません。 `--global` と `--tool-path` の両方を省略すると、ローカル ツールが一覧表示されます。

## <a name="examples"></a>使用例

- **`dotnet tool list -g`**

  お使いのコンピューター (現在のユーザー プロファイル) 上でユーザー全体にインストールされているすべてのグローバル ツールを一覧表示します。

- **`dotnet tool list --tool-path c:\global-tools`**

  特定の Windows ディレクトリからグローバル ツールを一覧表示します。

- **`dotnet tool list --tool-path ~/bin`**

  特定の Linux/macOS ディレクトリからグローバル ツールを一覧表示します。

- **`dotnet tool list`** または **`dotnet tool list --local`**

  現在のディレクトリで使用可能なすべてのローカル ツールを一覧表示します。

## <a name="see-also"></a>関連項目

- [.NET ツール](global-tools.md)
- [チュートリアル: .NET CLI を使って .NET グローバル ツールをインストールして使用する](global-tools-how-to-use.md)
- [チュートリアル: .NET CLI を使って .NET ローカル ツールをインストールして使用する](local-tools-how-to-use.md)
