---
title: Linux ディストリビューションに .NET をインストールする
description: Linux への .NET のインストールをサポートしている Linux ディストリビューションについて説明します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 6354ef6f0f9af2126312683893d6705b3b4c70f4
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594520"
---
# <a name="install-net-on-linux"></a>Linux に .NET をインストールする

> [!div class="op_single_selector"]
>
> - [Windows へのインストール](windows.md)
> - [macOS へのインストール](macos.md)
> - [Linux にインストールする](linux.md)

.NET は、さまざまな Linux ディストリビューションで使用できます。 ほとんどの Linux プラットフォームおよびディストリビューションには毎年メジャー リリースがあり、そのほとんどでは .NET のインストールに使用するパッケージ マネージャーが提供されます。 この記事では、現在何がサポートされているかと、どのパッケージ マネージャーが使用されるかについて説明します。

この記事の残りの部分では、.NET でサポートされている主要な各 Linux ディストリビューションの詳細について説明します。 すべての .NET リリースは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、Linux ディストリビューションのバージョンがサポート終了になるまでサポートされます。

互換性を最大限に高めるために、長期的なリリース (LTS) のバージョンを選択してください。

## <a name="unsupported-releases"></a>サポートされていないリリース

次のバージョンの .NET は、❌ サポート対象外となりました。 これらのダウンロードは、まだ公開されています。

- 3.0
- 2.2
- 2.0

これらのサポートされていないバージョンについては、以下のセクションでは詳しく説明しません。これらをインストールしようとする場合、実現できることが変動する可能性があります。

## <a name="alpine"></a>Alpine

Alpine には、インストーラーはありません。 [インストール スクリプト](linux-alpine.md#scripted-install)を使用するか、[手動でのインストール](linux-alpine.md#manual-install)手順に従う必要があります。

次の表に、現在サポートされている .NET リリースと、それらがサポートされている Alpine のバージョンの一覧を示します。 これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Alpine のバージョンの有効期限が切れるまで](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)サポートされます。

- ✔️ は、Alpine または .NET のバージョンがまだサポートされていることを示します。
- ❌ は、Alpine または .NET のバージョンがその Alpine のリリースではサポートされていないことを示します。
- Alpine のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| Alpine                      | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|-----------------------------|---------------|---------------|----------------|
| ✔️ [3.12](linux-alpine.md)  | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [3.11](linux-alpine.md)  | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [3.10](linux-alpine.md)  | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [3.9](linux-alpine.md)   | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [3.8](linux-alpine.md)   | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |

詳細については、[Alpine での .NET のインストール](linux-alpine.md)に関する記事をご覧ください。

## <a name="centos"></a>CentOS

CentOS 7 ではパッケージ マネージャーとして Yum が使用され、CentOS 8 では DNF が使用されます。

CentOS 7 と CentOS 8 の両方で現在サポートされている .NET のリリースの一覧は、次の表のとおりです。 これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、CentOS のバージョンがサポート終了になるまでサポートされます。

| CentOS                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |

詳細については、[CentOS での .NET のインストール](linux-centos.md)に関する記事をご覧ください。

## <a name="debian"></a>Debian

Debian では、パッケージ マネージャーとして APT (Advanced Package Tool) が使用されます。

次の表は、現在サポートされている .NET リリースと、それらがサポートされている Debian のバージョンの一覧です。 これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Debian のバージョンの有効期限が切れる](https://wiki.debian.org/DebianReleases)までサポートされます。

- ✔️ は、Debian または .NET のバージョンがまだサポートされていることを示します。
- ❌ は、Debian または .NET のバージョンがその Debian のリリースではサポートされていないことを示しています。
- Debian のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| Debian                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ❌ [8](linux-debian.md#debian-8-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |

詳細については、[Debian での .NET のインストール](linux-debian.md)に関する記事をご覧ください。

## <a name="fedora"></a>Fedora

Fedora では、パッケージ マネージャーとして DNF が使用されます。

現在サポートされている .NET リリースと、それらがサポートされている Fedora のバージョンの一覧は、次の表のとおりです。 これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Fedora のバージョンがサポート終了になる](https://fedoraproject.org/wiki/End_of_life)までサポートされます。

- ✔️ は、Fedora または .NET のバージョンがまだサポートされていることを示します。
- ❌ は、Fedora または .NET のバージョンがその Fedora のリリースではサポートされていないことを示しています。
- Fedora のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| Fedora                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [33](linux-fedora.md#fedora-33-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ❌ [31](linux-fedora.md#fedora-31-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [30](linux-fedora.md#fedora-30-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [29](linux-fedora.md#fedora-29-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [28](linux-fedora.md#fedora-28-) | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ❌ [27](linux-fedora.md#fedora-27-) | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |

詳細については、[Fedora での .NET のインストール](linux-fedora.md)に関する記事をご覧ください。

## <a name="opensuse"></a>openSUSE

openSUSE では、パッケージ マネージャーとして zypper が使用されます。

次の表は、openSUSE 15 で現在サポートされている .NET リリースの一覧です。 これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、openSUSE のバージョンがサポート終了になるまでサポートされます。

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |

詳細については、[openSUSE での .NET のインストール](linux-opensuse.md)に関する記事をご覧ください。

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux (RHEL) では、パッケージ マネージャーとして yum (RHEL 7) と DNF (RHEL 8) が使用されます。

RHEL 7 と RHEL 8 の両方で現在サポートされている .NET のリリースの一覧は、次の表のとおりです。 これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、RHEL のバージョンがサポート終了になるまでサポートされます。

- ✔️ は、RHEL または .NET のバージョンがまだサポートされていることを示します。
- ❌ は、RHEL または .NET のバージョンがその RHEL のリリースではサポートされていないことを示しています。
- RHEL のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| RHEL                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [7](linux-rhel.md#rhel-7--net-50) | ✔️ 2.1        | ✔️ [3.1](linux-rhel.md#rhel-7--net-core-31)        | ✔️ [5.0](linux-rhel.md#rhel-7--net-50) |

詳細については、[RHEL での .NET のインストール](linux-rhel.md)に関する記事をご覧ください。

## <a name="sles"></a>SLES

SLES では、パッケージ マネージャーとして zypper が使用されます。

次の表は、SLES 12 SP2 と SLES 15 の両方で現在サポートされている .NET リリースの一覧です。 これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、SLES のバージョンがサポート終了になるまでサポートされます。

- ✔️ は、SLES または .NET のバージョンがまだサポートされていることを示します。
- ❌ は、SLES または .NET のバージョンがその SLES のリリースではサポートされていないことを示しています。
- SLES のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [12 SP2](linux-sles.md#sles-12-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |

詳細については、[SLES での .NET のインストール](linux-sles.md)に関する記事をご覧ください。

## <a name="ubuntu"></a>Ubuntu

Ubuntu では、パッケージ マネージャーとして APT (Advanced Package Tool) が使用されます。

次の表は、Ubuntu と .NET のサポートの状態を示しています。

- ✔️ は、Ubuntu または .NET のバージョンがまだサポートされていることを示します。
- ❌ は、Ubuntu または .NET のバージョンがその Ubuntu のリリースではサポートされていないことを示しています。
- Ubuntu のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20.10](linux-ubuntu.md#2010-)       | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [20.04 (LTS)](linux-ubuntu.md#2004-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ❌ [19.10](linux-ubuntu.md#1910-)       | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ❌ [19.04](linux-ubuntu.md#1904-)       | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [18.10](linux-ubuntu.md#1810-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ✔️ [18.04 (LTS)](linux-ubuntu.md#1804-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ❌ [17.10](linux-ubuntu.md#1710-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ❌ [17.04](linux-ubuntu.md#1704-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ❌ [16.10](linux-ubuntu.md#1610-)       | ❌ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ✔️ [16.04 (LTS)](linux-ubuntu.md#1604-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |

詳細については、[Ubuntu での .NET のインストール](linux-ubuntu.md)に関する記事をご覧ください。

## <a name="next-steps"></a>次のステップ

- [.NET が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md?pivots=os-linux)。
- [チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。
- [チュートリアル: .NET アプリのコンテナー化](../docker/build-container.md)。
