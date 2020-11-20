---
title: Alpine に .NET をインストールする - .NET
description: Alpine に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 29901cc24ddd4bbe8200a36765ddd29f501394c0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506813"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a>Alpine に .NET SDK または .NET ランタイムをインストールする

この記事では、Alpine に .NET をインストールする方法について説明します。 Alpine のバージョンがサポート対象外である場合、.NET もそのバージョンでサポート対象外となります。 ただし、サポート対象外の場合でも、これらの手順がそれらのバージョンで .NET を実行するのに役立つことがあります。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

Alpine には、インストーラーはありません。 [インストール スクリプト](#scripted-install)を使用するか、[手動でのインストール](#manual-install)手順に従う必要があります。

## <a name="supported-distributions"></a>サポートされているディストリビューション

次の表に、現在サポートされている .NET リリースと、それらがサポートされている Alpine のバージョンの一覧を示します。 これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Alpine のバージョンの有効期限が切れるまで](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)サポートされます。

- ✔️ は、Alpine または .NET のバージョンがまだサポートされていることを示します。
- ❌ は、Alpine または .NET のバージョンがその Alpine のリリースではサポートされないことを示します。
- Alpine のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| Alpine  | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|-------- |---------------|---------------|----------------|
| ✔️ 3.12 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ 3.11 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ 3.10 | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ 3.9  | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ 3.8  | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |

次のバージョンの .NET は、サポート対象外となりました。 これらのダウンロードは、まだ公開されています。

- 3.0
- 2.2
- 2.0

## <a name="dependencies"></a>依存関係

Alpine Linux 上の .NET には、次の依存関係がインストールされている必要があります。

- icu-libs
- krb5-libs
- libgcc
- libintl
- libssl1.1 (Alpine v3.9 以上)
- libssl1.0 (Alpine v3.8 以下)
- libstdc++
- zlib

## <a name="scripted-install"></a>スクリプトでのインストール

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動インストール

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>次の手順

- [チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する](../tutorials/with-visual-studio-code.md)
