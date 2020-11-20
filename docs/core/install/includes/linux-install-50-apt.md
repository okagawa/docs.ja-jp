---
ms.openlocfilehash: 87c7abf6a20dd8e9769f3b3b3cbe271d32fd62c3
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507000"
---

### <a name="install-the-sdk"></a>SDK のインストール

.NET SDK を使用すると、.NET を使用してアプリを開発できます。 .NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。 .NET SDK をインストールするには、次のコマンドを実行します。

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

> [!IMPORTANT]
> "**パッケージ dotnet-sdk-5.0 が見つかりません**" のようなエラー メッセージが表示される場合は、「[APT のトラブルシューティング](#apt-troubleshooting)」セクションをご覧ください。

### <a name="install-the-runtime"></a>ランタイムをインストールする

ASP.NET Core ランタイムを使用すると、ランタイムを提供しない .NET を使用して作成されたアプリを実行できます。 次のコマンドを実行すると、.NET の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-5.0
```

> [!IMPORTANT]
> "**パッケージ aspnetcore-runtime-5.0 が見つかりません**" のようなエラー メッセージが表示される場合は、「[APT のトラブルシューティング](#apt-troubleshooting)」セクションをご覧ください。

ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET ランタイムをインストールできます。それには、前のコマンドの `aspnetcore-runtime-5.0` を `dotnet-runtime-5.0` で置き換えます。

```bash
sudo apt-get install -y dotnet-runtime-5.0
```
