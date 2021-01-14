---
title: Snap を使用して Linux に .NET をインストールする - .NET
description: Snap を使用して Linux に .NET SDK または .NET ランタイムをインストールする方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 741933b5ca6f01d73b388675fe7f8a43c4efb0f9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970928"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a>Snap を使用して .NET SDK または .NET ランタイムをインストールする

Snap パッケージを使用して、.NET SDK または .NET ランタイムをインストールします。 Snap は、Linux ディストリビューションに組み込まれているパッケージ マネージャーに代わる優れた方法です。 この記事では、[Snap](https://snapcraft.io/dotnet-sdk) を使用して .NET をインストールする方法について説明します。

Snap は、アプリとその依存関係のバンドルであり、さまざまな Linux ディストリビューション間で変更を加えることなく動作します。 Snap は、Snap Store で見つけてインストールできます。 Snap の詳細については、[Snap の概要](https://snapcraft.io/docs/getting-started)に関するページをご覧ください。

> [!CAUTION]
> Snap パッケージは、Windows 10 の WSL2 ではサポートされていません。 別の方法としては、[`dotnet-install` スクリプト](linux-scripted-manual.md#scripted-install)または特定の WSL2 ディストリビューション用のパッケージ マネージャーを使用します。 推奨されませんが、[snapcraft フォーラムからサポートされていない回避策](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033)を使用して Snap を有効にしてみることができます。

## <a name="net-releases"></a>.NET のリリース

Snap では、✔️ サポートされているバージョンの .NET SDK のみを利用できます。 .NET ランタイムのすべてのバージョンは、バージョン 2.1 以降の Snap から使用できます。 次の表は、.NET (および .NET Core) のリリースの一覧です。

| ✔️ Supported | ❌ サポートされていない |
|-------------|---------------|
| 5.0         | 3.0           |
| 3.1 (LTS)   | 2.2           |
| 2.1 (LTS)   | 2.0           |
|             | 1.1           |
|             | 1.0           |

.NET リリースのライフ サイクルの詳細については、「[.NET Core と .NET 5 のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」を参照してください。

## <a name="sdk-or-runtime"></a>SDK またはランタイム

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a>SDK のインストール

.NET SDK 用の Snap パッケージはすべて、同じ識別子 `dotnet-sdk` で公開されます。 特定のバージョンの SDK は、チャネルを指定することによってインストールできます。 SDK には、対応するランタイムが含まれています。 次の表に、チャネルの一覧を示します。

| .NET のバージョン | Snap パッケージまたはチャネル  |
|--------------|--------------------------|
| 5.0          | `5.0` または `latest/stable` |
| 3.1 (LTS)    | `3.1` または `lts/stable`    |
| 2.1 (LTS)    | `2.1`                    |

`snap install` コマンドを使用して、.NET SDK の Snap パッケージをインストールします。 `--channel` パラメーターを使用して、インストールするバージョンを指定します。 このパラメーターを省略すると、`latest/stable` が使用されます。 この例では、`5.0` が指定されています。

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

次に、`snap alias` コマンドを使用して、システムの `dotnet` コマンドを登録します。

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

このコマンドの形式は次のとおりです: `sudo snap alias {package}.{command} {alias}`。 `{alias}` の名前は自由に選択できます。 たとえば、snap によってインストールされた特定のバージョンにちなんでコマンドの名前を指定できます: `sudo snap alias dotnet-sdk.dotnet dotnet50`。 コマンド `dotnet50` を使用すると、この特定のバージョンの .NET が呼び出されます。 ただし、異なるエイリアスの選択は、ほとんどのチュートリアルや例と互換性がありません。それらでは、`dotnet` コマンドを使用することが想定されているためです。

## <a name="install-the-runtime"></a>ランタイムをインストールする

.NET ランタイム用の Snap パッケージはそれぞれ、独自のパッケージ識別子で公開されます。 次の表に、パッケージ識別子の一覧を示します。

| .NET のバージョン      | Snap パッケージ        |
|-------------------|---------------------|
| 5.0               | `dotnet-runtime-50` |
| 3.1 (LTS)         | `dotnet-runtime-31` |
| 3.0               | `dotnet-runtime-30` |
| 2.2               | `dotnet-runtime-22` |
| 2.1 (LTS)         | `dotnet-runtime-21` |

`snap install` コマンドを使用して、.NET ランタイムの Snap パッケージをインストールします。 この例では、.NET 5.0 がインストールされます。

```bash
sudo snap install dotnet-runtime-50 --classic
```

次に、`snap alias` コマンドを使用して、システムの `dotnet` コマンドを登録します。

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

コマンドの形式は次のとおりです: `sudo snap alias {package}.{command} {alias}`。 `{alias}` の名前は自由に選択できます。 たとえば、snap によってインストールされた特定のバージョンにちなんでコマンドの名前を指定できます: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`。 コマンド `dotnet50` を使用すると、特定のバージョンの .NET が呼び出されます。 ただし、異なるエイリアスの選択は、ほとんどのチュートリアルや例と互換性がありません。それらでは、`dotnet` コマンドを使用できることが想定されているためです。

## <a name="tlsssl-certificate-errors"></a>TLS/SSL 証明書のエラー

Snap を使用して .NET をインストールする場合、一部のディストリビューションでは .NET の TLS/SSL 証明書が見つからないことがあり、`restore` の間にエラーが表示される可能性があります。

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

この問題を解決するには、いくつかの環境変数を設定します。

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

証明書の場所は、ディストリビューションによって異なります。 次に、問題が発生したディストリビューションの場所を示します。

| Distribution | 場所                                            |
|--------------|-----------------------------------------------------|
| **Fedora**   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| **OpenSUSE** | `/etc/ssl/ca-bundle.pem`                            |
| **Solus**    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a>次のステップ

- [.NET CLI のタブ補完を有効にする方法](../tools/enable-tab-autocomplete.md)
- [チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する](../tutorials/with-visual-studio-code.md)
