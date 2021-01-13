---
title: NETSDK1005 および NETSDK1047:アセット ファイルにターゲットがありません
description: ターゲットがないアセット ファイルの問題を解決する方法。
author: sfoslund
ms.topic: error-reference
ms.date: 12/17/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: e3e7389adf6a9a715d44661a5f7cbae5efe299e4
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678172"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a>NETSDK1005 および NETSDK1047:アセット ファイルにターゲットがありません

**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン

.NET SDK でエラー NETSDK1005 または NETSDK1047 が発生した場合、プロジェクトのアセット ファイルには、ターゲット フレームワークのいずれかに関する情報が存在しません。 NuGet によって、*project.assets.json* という名前のファイルが *obj* フォルダーに書き込まれます。これはコンパイラに渡すパッケージに関する情報を取得するために .NET SDK によって使用されます。 .NET 5 では、NuGet で `TargetFrameworkAlias` という名前の新しいフィールドが追加されたため、以前のバージョンの MSBuild または NuGet では、新しいフィールドのないアセット ファイルが生成されます。 詳細については、[エラー NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html) に関するページを参照してください。

このエラーを解決するために実行できるアクションをいくつか次に示します。

* MSBuild バージョン 16.8 以降および NuGet バージョン 5.8 以降を使用していることを確認し、ツールを更新した後でプロジェクトを復元します。 NuGet バージョン 5.8 以降を使用している場合は、Visual Studio 2019 バージョン 16.8 以降、MSBuild バージョン 16.8 以降、.NET 5.0 SDK 以降を使用する必要があります。

* バージョン 16.8 をインストールした後、またはプロジェクトのターゲット フレームワークを変更した後に、Visual Studio 2019 でプロジェクトを初めてビルドするときにエラーが発生した場合は、プロジェクトをもう一度ビルドします。

* プロジェクトをビルドする前に、*obj* フォルダーを削除します。

* 見つからないターゲット値がプロジェクトの `TargetFrameworks` プロパティに含まれていることを確認します。
