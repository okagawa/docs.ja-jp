---
ms.openlocfilehash: 540eebd957ce8ce0928db2bd8317cb220cba30bb
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031770"
---

[dotnet-install スクリプト](../../tools/dotnet-install-script.md)は、**SDK** および **ランタイム** のインストールの自動化および管理者以外によるインストールのために使用されます。 このスクリプトは <https://dot.net/v1/dotnet-install.sh> からダウンロードできます。

スクリプトでは、最新の SDK の[長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) が既定でインストールされます。 (LTS) バージョンではない場合がある現在のリリースをインストールするには、`-c Current` パラメーターを使用します。

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
