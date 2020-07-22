---
title: Azure VM に ASP.NET Web アプリを移行する
description: ASP.NET Web アプリケーションをオンプレミスから Azure 仮想マシンに移行する方法について説明します。
ms.topic: how-to
ms.date: 06/20/2020
ms.openlocfilehash: 5ef340d020b72bebe46fe598fe68e7d02d0c0363
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174245"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>Azure 仮想マシンへの ASP.NET Web アプリケーションの移行

このドキュメントでは、ASP.NET Web アプリケーションをオンプレミスから Azure 仮想マシンに移行する方法の概要を説明します。

## <a name="quickstart"></a>クイック スタート

仮想マシンを作成し、この仮想マシンにアプリを発行する方法について説明します。[Azure VM への発行](https://tutorials.visualstudio.com/aspnet-vm/intro)

## <a name="get-started"></a>はじめに

次のチュートリアルでは、仮想マシンを作成 (または移行) する手順、Web アプリケーションを発行する手順、Azure でアプリケーションをサポートするために必要なその他のタスクについて説明しています。

- 次の方法のいずれかを使用して、Azure に ASP.NET アプリケーション用の仮想マシンを作成します。
  - [ASP.NET アプリケーション用の新しい仮想マシンを作成する](https://go.microsoft.com/fwlink/?linkid=863237)
  - [オンプレミスの既存の VMWare 仮想マシンを移行する](/azure/migrate/tutorial-migrate-vmware)
  - [オンプレミスの既存の Hyper-V 仮想マシンを移行する](/azure/migrate/tutorial-migrate-hyper-v)
- [Visual Studio を使用してアプリを発行する](https://go.microsoft.com/fwlink/?linkid=863240)
- [VM 用のセキュリティで保護された仮想ネットワークを作成する](/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [アプリケーションの CI/CD パイプラインを作成する](/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [高可用性とスケーラビリティを確保するために VM スケール セットに移行する](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a>注意事項

### <a name="benefits"></a>利点

仮想マシンを使用すると、アプリケーションをオンプレミスからクラウドに最も簡単に移行できます。 仮想マシンを使用することで、アプリケーションがオンプレミスで使用している環境をレプリケートできると同時に、独自のデータ センターを管理する必要性が排除されます。 Virtual Machine Scale Sets は、Virtual Machines で実行されているアプリケーションの高可用性とスケーラビリティを実現します。

### <a name="virtual-machine-size"></a>仮想マシンのサイズ

ワークロードに最も最適化された仮想マシンのサイズと種類を選択します。 詳細については、「[Azure の Windows 仮想マシンのサイズ](/azure/virtual-machines/windows/sizes)」をご覧ください。

### <a name="maintenance"></a>メンテナンス 

オンプレミス コンピューターと同様に、仮想マシンの管理と更新はユーザーが行う必要があります<sup>&#42;</sup>。 [Azure App Service](/azure/app-service/) や[コンテナー](/azure/app-service/containers/)などのサービスとしてのプラットフォーム (PaaS) 環境でアプリケーションを実行できる場合、その必要はなくなります。

*<sup>&#42;</sup>[仮想マシン スケール セットの OS の自動アップグレード](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)は、現在、プレビュー サービスとして提供されています。*

### <a name="virtual-networks"></a>仮想ネットワーク

Azure Virtual Network を使用すると、次のことが可能になります。

- 制御可能なハイブリッド インフラストラクチャを構築する
- 独自の IP アドレスと DNS サーバーを使用する
- アプリケーション用に安全性の高い分離された環境を作成する
- 複数の[接続オプション](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)のいずれかを使用して、VM をオンプレミス ネットワークに接続する
- [ExpressRoute](https://azure.microsoft.com/services/expressroute/) を使用して、仮想マシンをオンプレミス ネットワークに統合する

作業を開始するには、「[Virtual Network のドキュメント](/azure/virtual-network/)」をご覧ください。

### <a name="active-directory"></a>Active Directory
多くのアプリケーションでは、認証と ID 管理に Active Directory を使用しています。

- Azure AD Connect を使用すると、オンプレミスのディレクトリを Azure Active Directory と統合できます。 作業を開始するには、「[オンプレミスのディレクトリと Azure Active Directory の統合](/azure/active-directory/connect/active-directory-aadconnect)」をご覧ください。
- [ExpressRoute](https://azure.microsoft.com/services/expressroute/) を使用すると、アプリケーションはオンプレミスの Active Directory にアクセスできます。

### <a name="sql-databases"></a>SQL データベース

アプリケーションがオンプレミス データベースを使用している場合、既定ではアプリはデータベースと対話できません。 次のいずれかを実行できます。

- アプリケーションがオンプレミスで実行されているデータベースにアクセスできるようにするためのハイブリッド ネットワークを構成する。
- データベースを Azure に移行する。 詳細については、[Azure への SQL Server データベースの移行](sql.md)に関する記事をご覧ください。

### <a name="high-availability-and-scalability"></a>高可用性とスケーラビリティ

#### <a name="virtual-machine-scale-sets"></a>Virtual Machine Scale Sets
アプリケーションの高可用性とスケーラビリティを確保する場合、VM イメージを Azure 仮想マシン スケール セットに移行すると、アプリケーションの可用性とスケーラビリティが向上します。 VM Scale Sets では、構成済みの既存の VM を使用したり、アプリケーションでイメージをビルドするためのビルド パイプラインを設定したりできます。

作業を開始するには、「[仮想マシン スケール セットへのアプリケーションのデプロイ](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)」をご覧ください。

#### <a name="centralized-logging"></a>ログの一元化
複数のインスタンスでアプリケーションを実行する場合は、[Azure Storage](/azure/storage/) などの一元化された場所にログを保存することを検討します。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [Azure への SQL Server データベースの移行](sql.md)
