---
title: RHEL に .NET をインストールする - .NET
description: RHEL に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 0b6138185bfd3e2f50c1b31e82779165715a5b6e
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851641"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a>RHEL に .NET SDK または .NET ランタイムをインストールする

.NET は RHEL でサポートされています。 この記事では、RHEL に .NET をインストールする方法について説明します。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>ご利用の Red Hat サブスクリプションを登録する

Red Hat から RHEL に .NET をインストールするには、まず、Red Hat Subscription Manager を使用して登録する必要があります。 ご利用のシステムでまだこれを行っていない場合、または不明な場合は、[.NET 向けの Red Hat の製品ドキュメント](https://access.redhat.com/documentation/net/5.0/)を参照してください。

## <a name="supported-distributions"></a>サポートされているディストリビューション

RHEL 7 と RHEL 8 の両方で現在サポートされている .NET のリリースの一覧は、次の表のとおりです。 これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、RHEL のバージョンがサポート終了になるまでサポートされます。

- ✔️ は、RHEL または .NET のバージョンがまだサポートされていることを示します。
- ❌ は、RHEL または .NET のバージョンがその RHEL のリリースではサポートされていないことを示しています。
- RHEL のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| RHEL                     | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#rhel-8-)        | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [7](#rhel-7--net-50) | ✔️ 2.1        | ✔️ [3.1](#rhel-7--net-core-31)        | ✔️ [5.0](#rhel-7--net-50) |

次のバージョンの .NET は、サポート対象外となりました。 これらのダウンロードは、まだ公開されています。

- 3.0
- 2.2
- 2.0

## <a name="remove-preview-versions"></a>プレビュー バージョンの削除

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a>その他のバージョンをインストールする方法

.NET の他のリリースをインストールするために必要な手順については、[.NET 向けの Red Hat のドキュメント](https://access.redhat.com/documentation/net/5.0/)を参照してください。

## <a name="rhel-8-"></a>RHEL 8 ✔️

.NET は、RHEL 8 用の AppStream リポジトリに含まれています。

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a>RHEL 7 ✔️ .NET 5.0

次のコマンドでは、`scl-utils` パッケージがインストールされます。

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>SDK のインストール

.NET SDK を使用すると、.NET を使用してアプリを開発できます。 .NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。 .NET SDK をインストールするには、次のコマンドを実行します。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

Red Hat では、`rh-dotnet50` を永続的に有効にすることは推奨されません。他のプログラムに影響を与える可能性があるためです。 `rh-dotnet` を永続的に有効にする場合は、 _~/.bashrc_ ファイルに次の行を追加します。

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a>ランタイムをインストールする

.NET ランタイムを使用すると、ランタイムを含まない .NET を使用して作成されたアプリを実行できます。 次のコマンドを実行すると、.NET Core の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。 ご利用のターミナルで、次のコマンドを実行します。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50 bash
```

Red Hat では、`rh-dotnet50` を永続的に有効にすることは推奨されません。他のプログラムに影響を与える可能性があるためです。 `rh-dotnet50` を永続的に有効にする場合は、 _~/.bashrc_ ファイルに次の行を追加します。

```bash
source scl_source enable rh-dotnet50
```

ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET ランタイムをインストールできます。それには、前述のコマンドの `rh-dotnet50-aspnetcore-runtime-5.0` を `rh-dotnet50-dotnet-runtime-5.0` で置き換えます。

## <a name="rhel-7--net-core-31"></a>RHEL 7 ✔️ .NET Core 3.1

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

次のコマンドでは、`scl-utils` パッケージがインストールされます。

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>SDK のインストール

.NET Core SDK を使用すると、.NET Core を使用してアプリを開発できます。 .NET Core SDK をインストールする場合、対応するランタイムをインストールする必要はありません。 .NET Core SDK をインストールするには、次のコマンドを実行します。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

Red Hat では、`rh-dotnet31` を永続的に有効にすることは推奨されません。他のプログラムに影響を与える可能性があるためです。 たとえば、`rh-dotnet31` には、ベースとなる RHEL のバージョンとは異なるバージョンの `libcurl` が含まれています。 これにより、異なるバージョンの `libcurl` を想定していないプログラムで問題が発生する可能性があります。 `rh-dotnet` を永続的に有効にする場合は、 _~/.bashrc_ ファイルに次の行を追加します。

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a>ランタイムをインストールする

.NET Core ランタイムを使用すると、ランタイムを含まない .NET Core を使用して作成されたアプリを実行できます。 次のコマンドを実行すると、.NET Core の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。 ご利用のターミナルで、次のコマンドを実行します。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

Red Hat では、`rh-dotnet31` を永続的に有効にすることは推奨されません。他のプログラムに影響を与える可能性があるためです。 たとえば、`rh-dotnet31` には、ベースとなる RHEL のバージョンとは異なるバージョンの `libcurl` が含まれています。 これにより、異なるバージョンの `libcurl` を想定していないプログラムで問題が発生する可能性があります。 `rh-dotnet31` を永続的に有効にする場合は、 _~/.bashrc_ ファイルに次の行を追加します。

```bash
source scl_source enable rh-dotnet31
```

ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET Core ランタイムをインストールできます。それには、前述のコマンドの `rh-dotnet31-aspnetcore-runtime-3.1` を `rh-dotnet31-dotnet-runtime-3.1` で置き換えます。

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>依存関係

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a>スクリプトでのインストール

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動インストール

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>次の手順

- [チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する](../tutorials/with-visual-studio-code.md)
