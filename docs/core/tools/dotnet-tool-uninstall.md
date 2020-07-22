---
title: dotnet tool uninstall コマンド
description: dotnet tool uninstall コマンドでは、お使いのコンピューター上から指定された .NET Core ツールをアンインストールします。
ms.date: 02/14/2020
ms.openlocfilehash: 0416f91019a49e17f1be14a1d928ad1fafaa736c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463311"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン

## <a name="name"></a>名前

`dotnet tool uninstall` - お使いのコンピューター上から指定された [.NET Core ツール](global-tools.md)をアンインストールします。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a>説明

`dotnet tool uninstall` コマンドでは、お使いのコンピューター上から .NET Core ツールをアンインストールするための方法を提供します。 コマンドを使用するには、次のいずれかのオプションを指定します。

* 既定の場所にインストールされたグローバル ツールをアンインストールするには、`--global` オプションを使用します。
* カスタムの場所にインストールされたグローバル ツールをアンインストールするには、`--tool-path` オプションを使用します。
* ローカル ツールをアンインストールするには、`--global` および `--tool-path` オプションを省略します。

**ローカル ツールは .NET Core SDK 3.0 以降で使用できます。**

## <a name="arguments"></a>引数

- **`PACKAGE_NAME`**

  アンインストールする .NET Core ツールが格納されている NuGet パッケージの名前または ID。 パッケージを見つけるには、[dotnet tool list](dotnet-tool-list.md) コマンドを使用できます。

## <a name="options"></a>オプション

- **`-g|--global`**

  ツールがユーザー全体のインストールから削除されることを指定します。 `--tool-path` オプションと組み合わせることはできません。 `--global` と `--tool-path` の両方を省略すると、削除されるツールはローカル ツールであると指定されます。

- **`-h|--help`**

  コマンドの短いヘルプを印刷します。

- **`--tool-path <PATH>`**

  ツールをアンインストールする場所を指定します。 PATH は絶対パスでも相対パスでもかまいません。 `--global` オプションと組み合わせることはできません。 `--global` と `--tool-path` の両方を省略すると、削除されるツールはローカル ツールであると指定されます。

## <a name="examples"></a>使用例

- **`dotnet tool uninstall -g dotnetsay`**

  [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  特定の Windows ディレクトリから [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  特定の Linux/macOS ディレクトリから [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。

- **`dotnet tool uninstall dotnetsay`**

  現在のディレクトリから [dotnetsay](https://www.nuget.org/packages/dotnetsay/) ローカル ツールをアンインストールします。

## <a name="see-also"></a>関連項目

- [.NET Core ツール](global-tools.md)
- [チュートリアル: .NET Core CLI を使って .NET Core グローバル ツールをインストールして使用する](global-tools-how-to-use.md)
- [チュートリアル: .NET Core CLI を使って .NET Core ローカル ツールをインストールして使用する](local-tools-how-to-use.md)
