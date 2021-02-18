---
title: NETSDK1064:パッケージが見つかりません
description: パッケージが見つからない場合に発生する、.NET SDK エラー NETSDK1064 について説明します。
ms.topic: error-reference
ms.date: 02/10/2021
f1_keywords:
- NETSDK1064
ms.openlocfilehash: 1a155db1aacbceb9878401dbcac61ece5f1f9824
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488205"
---
# <a name="netsdk1064-package-not-found"></a>NETSDK1064:パッケージが見つかりません

**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン

このエラーは、プロジェクトのビルドに必要な NuGet パッケージをビルド ツールが見つけることができない場合に発生します。 通常、これの原因はパッケージの復元の問題です。 完全なエラー メッセージは、次の例のようになります。

> NETSDK1064:パッケージ 'PackageName'、バージョン x.x.x が見つかりませんでした。 NuGet の復元以降に削除された可能性があります。 または、パスの最大長の制限が原因で、NuGet の復元が一部しか完了していない可能性があります。

このエラーの解決には、次のいくつかのアクションを実行します。

* お使いの *MSBuild.exe* コマンドに `/restore` オプションを追加します。 軽度のバグが発生する可能性があるため、`/t:Restore;Build` は使用しないでください。 パッケージが自動的に復元されるため、代わりに `dotnet build` コマンドを使用することもできます。
* Visual Studio 2019 または *MSBuild.exe* を使用してパッケージの復元を実行した場合、パスの最大長の制限によりエラーが発生している可能性があります。 詳細については、「[長いパスのサポート (NuGet CLI)](/nuget/reference/cli-reference/cli-ref-long-path)」と [NuGet/Home のイシュー 3324](https://github.com/NuGet/Home/issues/3324) に関するページを参照してください。
* 復元を x86 の *nuget.exe* で行い、ビルドを x64 の *MSBuild.exe* で行っている場合、このエラーはビットの不一致により発生している可能性があります。 *project.assets.json* のパスは別のビットのプロセスでは動作しないため、復元が取得したとするパッケージがビルドで検出されません。 このエラーを解決するには、復元とビルドに同じビットのツールを使用するか、x86 と x64 間で仮想化されないフォルダーにパッケージを復元するよう NuGet を構成します。 詳細については、[dotnet/core のイシュー 4332](https://github.com/dotnet/core/issues/4332) に関するページを参照してください。
* Docker イメージを構築している場合は、 *.dockerignore* ファイルで *bin* および *obj* ディレクトリが必ず無視されるようにしてください。 詳細については、「[NETSDK1064:Package DnsClient, 1.2.0 was not found](https://stackoverflow.com/questions/61167032/error-netsdk1064-package-dnsclient-1-2-0-was-not-found)」 (Package DnsClient 1.2.0 が見つからない) を参照してください。
