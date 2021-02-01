---
title: .NET コンテナーで対象とする OS
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | .NET コンテナーで対象とする OS'
ms.date: 01/13/2021
ms.openlocfilehash: b128a7b98d7f46034a56314bd8cc6b4f5731f121
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957911"
---
# <a name="what-os-to-target-with-net-containers"></a>.NET コンテナーで対象とする OS

Docker でサポートされているオペレーティング システムの多様性と、.NET Framework と .NET 5 の違いを考慮し、使用しているフレームワークに応じて特定の OS と特定のバージョンをターゲットにする必要があります。

Windows の場合、Windows Server Core または Windows Nano Server を使用できます。 これらの Windows バージョンには、.NET Framework または .NET 5 でそれぞれ必要になる可能性がある異なる特性 (Windows Server Core の IIS と Nano Server の Kestrel のような自己ホスト型 Web サーバー) があります。

Linux の場合、複数のディストリビューションを利用できます。また、Linux は公式の .NET Docker イメージ (Debian など) でサポートされています。

図 3-1 では、使用されている .NET Framework に応じて利用可能な OS のバージョンを確認できます。

![どの .NET コンテナーでどの OS を使用するかを示す図。](./media/net-container-os-targets/targeting-operating-systems.png)

**図 3-1.** .NET Framework のバージョンに応じて対象にすることができるオペレーティング システム

.NET Framework のレガシー アプリケーションをデプロイする場合は、レガシー アプリと IIS と互換性がある、Windows Server Core をターゲットにする必要がありますが、より大きなイメージが含まれます。 .NET 5 アプリケーションをデプロイする場合は、クラウドに最適化され、Kestrel を使用し、小型で起動が速い Windows Nano Server をターゲットにすることができます。 Debian や Alpine などをサポートしている Linux もターゲットにすることができます。 同様に、Kestrel を使用し、より小さく起動が速くなります。

別の Linux ディストリビューションを使用したい場合や、Microsoft が提供していないバージョンのイメージが必要な場合は、独自の Docker イメージを作成することもできます。 たとえば、従来の .NET Framework と Windows Server Core 上で実行されている ASP.NET Core を使用してイメージを作成することができます (ただし、Docker の場合はあまり一般的ではないシナリオです)。

Dockerfile ファイルにイメージ名を追加すると、次の例のように、使用するタグに応じてオペレーティング システムとバージョンを選択できます。

| イメージ | コメント |
|-------|----------|
| mcr.microsoft.com/dotnet/runtime:5.0 | .NET 5 マルチアーキテクチャ: Docker ホストに応じて、Linux と Windows Nano Server をサポートします。 |
| mcr.microsoft.com/dotnet/aspnet:5.0 | ASP.NET Core 5.0 マルチアーキテクチャ: Docker ホストに応じて、Linux と Windows Nano Server をサポートします。 <br/> aspnetcore イメージでは、ASP.NET Core 用に 少しの最適化が行われています。 |
| mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim | Linux Debian ディストリビューションの .NET 5 ランタイムのみ |
| mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1809 | Windows Nano Server (Windows Server バージョン 1809) の .NET 5 ランタイムのみ |

> [!div class="step-by-step"]
> [前へ](container-framework-choice-factors.md)
> [次へ](official-net-docker-images.md)
