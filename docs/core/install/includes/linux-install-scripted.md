---
ms.openlocfilehash: 07dd58c314c826c426193b829ea1f64669fb888b
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594573"
---

[dotnet-install スクリプト](../../tools/dotnet-install-script.md)は、**SDK** および **ランタイム** のインストールの自動化および管理者以外によるインストールのために使用されます。 このスクリプトは <https://dot.net/v1/dotnet-install.sh> からダウンロードできます。

このスクリプトでは、最新の SDK の[長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET 3.1) が既定でインストールされます。 (LTS) バージョンではない場合がある現在のリリースをインストールするには、`-c Current` パラメーターを使用します。

```bash
./dotnet-install.sh -c Current
```

SDK の代わりに .NET ランタイムをインストールするには、`--runtime` パラメーターを使用します。

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

特定のバージョンをインストールするには、`-c` パラメーターを変更して特定のバージョンを指定します。 次のコマンドでは、.NET SDK 5.0 がインストールされます。

```bash
./dotnet-install.sh -c 5.0
```

詳細については、「[dotnet-install スクリプト リファレンス](../../tools/dotnet-install-script.md)」をご覧ください。
