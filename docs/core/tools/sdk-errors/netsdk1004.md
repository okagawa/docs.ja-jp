---
title: 'NETSDK1004: 資産ファイルが見つかりません'
description: .NET SDK エラー NETSDK1004 について学習します。これは、project.assets.json ファイルが見つからない場合に発生します。
ms.topic: error-reference
ms.date: 01/29/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: 8416063fe318106cbcb4dbccacef3ecaaff5bba2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216436"
---
# <a name="netsdk1004-assets-file-not-found"></a>NETSDK1004: 資産ファイルが見つかりません

**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン

NuGet によって、*project.assets.json* という名前のファイルが *obj* フォルダーに書き込まれます。これはコンパイラに渡すパッケージに関する情報を取得するために .NET SDK によって使用されます。 このエラーが発生するのは、資産ファイル *project.assets.json* がビルド中に見つからない場合です。 完全なエラー メッセージは、次の例のようになります。

**NETSDK1004: 資産ファイル 'C:\path\to\project.assets.json' が見つかりません。このファイルを生成するには、NuGet パッケージの復元を実行します。**

このエラーの原因として考えられるものをいくつか以下に示します。

* `%` 文字を含むディレクトリ パスから `dotnet build` コマンドを実行している。 このエラーを解決するには、フォルダー名から `%` を削除し、`dotnet build` を再実行します。
* プロジェクト ファイルに対する変更が、プロジェクト システムによって自動的に検出および復元されなかった。 このエラーを解決するには、コマンド プロンプトを開き、プロジェクトで `dotnet restore` を実行します。
* プロジェクトが、古いバージョンの Nuget.exe によって個別に復元された。 このエラーを解決するには、コマンド プロンプトを開き、プロジェクトで `dotnet restore` を実行します。
* NETSDK1045 (使用している SDK のバージョンでプロジェクトのターゲット フレームワークがサポートされていない) などの以前のエラーにより、NuGet でプロジェクト資産ファイルが作成されなかった。 NETSDK1004 エラーを解決するには、以前のエラーを解決してから、プロジェクトで `dotnet restore` を実行します。
* App Center CI で、NuGet にはない外部アセンブリを含むプロジェクトがビルドされている。 このエラーを解決するには、アセンブリの NuGet パッケージを使用します。
