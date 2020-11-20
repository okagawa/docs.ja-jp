---
ms.openlocfilehash: ed269683f5c4569c21ae53e9a3c1ec65eb5ebd43
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506853"
---

### <a name="install-the-sdk"></a>SDK のインストール

.NET SDK を使用すると、.NET を使用してアプリを開発できます。 .NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。 .NET SDK をインストールするには、次のコマンドを実行します。

```bash
sudo zypper install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a>ランタイムをインストールする

ASP.NET Core ランタイムを使用すると、ランタイムを提供しない .NET を使用して作成されたアプリを実行できます。 次のコマンドを実行すると、.NET の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。 ご利用のターミナルで、次のコマンドを実行します。

```bash
sudo zypper install aspnetcore-runtime-5.0
```

ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET ランタイムをインストールできます。それには、前のコマンドの `aspnetcore-runtime-5.0` を `dotnet-runtime-5.0` で置き換えます。

```bash
sudo zypper install dotnet-runtime-5.0
```
