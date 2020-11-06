---
ms.openlocfilehash: 2edb06106283c26573863f230e5e9956728cdfa3
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135649"
---

### <a name="install-the-sdk"></a>SDK のインストール

.NET Core SDK を使用すると、.NET Core を使用してアプリを開発できます。 .NET Core SDK をインストールする場合、対応するランタイムをインストールする必要はありません。 .NET Core SDK をインストールするには、次のコマンドを実行します。

```bash
sudo dnf install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a>ランタイムをインストールする

.NET Core ランタイムを使用すると、ランタイムを含まない .NET Core を使用して作成されたアプリを実行できます。 次のコマンドを実行すると、.NET Core の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo dnf install aspnetcore-runtime-3.1
```

ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET Core ランタイムをインストールできます。それには、前のコマンドの `aspnetcore-runtime-3.1` を `dotnet-runtime-3.1` で置き換えます。

```bash
sudo dnf install dotnet-runtime-3.1
```
