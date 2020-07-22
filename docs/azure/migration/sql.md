---
title: SQL Server データベースを Azure に移行する
description: SQL Server データベースをオンプレミスの SQL Server から Azure に移行する方法について説明します。
ms.topic: how-to
ms.date: 05/27/2020
ms.openlocfilehash: 5f191cafbff3823d04e1dbd1fdf81e1157e20999
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174284"
---
# <a name="migrate-a-sql-server-database-to-azure"></a>SQL Server データベースを Azure に移行する

この記事では、SQL Server データベースを Azure に移行するための 2 つの選択肢について概説します。 Azure では、運用 SQL Server データベースを移行するための主な選択肢が 3 つあります。 この記事では、次の 2 つの選択肢を中心に説明します。

1. [Azure VM 上の SQL Server](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): Azure で実行されている Windows 仮想マシンにインストールされ、ホストされている SQL Server インスタンス。これは、サービスとしてのインフラストラクチャ (IaaS) とも呼ばれます。
2. [Azure SQL Database](/azure/sql-database/sql-database-technical-overview):フル マネージドの Azure SQL データベース サービス。これは、サービスとしてのプラットフォーム (PaaS) とも呼ばれます。

それぞれに、移行前に評価する必要がある長所と短所があります。 3 番目の選択肢は、[Azure SQL Database Managed Instance](/azure/sql-database/sql-database-managed-instance) です。

## <a name="get-started"></a>作業開始

使用するサービスによっては、次の移行ガイドが役立ちます。

* [Azure VM の SQL Server への SQL Server データベースの移行](/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [SQL Server データベースを Azure SQL Database に移行する](/azure/sql-database/sql-database-migrate-your-sql-server-database)

さらに、概念説明への次のリンクが、VM の理解を深めるうえで役立ちます。

* [Azure 仮想マシンにおける SQL Server の高可用性とディザスター リカバリー](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Azure Virtual Machines における SQL Server のパフォーマンスに関するベスト プラクティス](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Azure Virtual Machines における SQL Server のアプリケーション パターンと開発計画](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

次のリンクは、Azure SQL Database データベースの理解を深めるうえで役立ちます。

* [Azure SQL Database のサーバーとデータベースを作成し、管理する](/azure/sql-database/sql-database-servers-databases)
* [データベース トランザクション ユニット (DTU) とエラスティック データベース トランザクション ユニット (eDTU)](/azure/sql-database/sql-database-what-is-a-dtu)
* [Azure SQL Database のリソース制限](/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a>IaaS または PaaS の選択

データベースの移行先を評価する際に、IaaS または PaaS のどちらがより適切かを判断します。

**次の状況に該当する場合は、Azure VM の SQL Server を選択します。**

* 変更を最小限に抑えて、データベースとアプリケーションを "リフトアンドシフト" する場合。
* データベース サーバーとそのサーバーが実行される VM を完全に制御する場合。
* 使用する SQL Server および Windows Server のライセンスが既にある場合。

**次の状況に該当する場合は、Azure SQL Database を選択します。**

* アプリケーションを最新化し、Azure の他の PaaS サービスを使用するために移行する場合。
* データベース サーバーとそのサーバーが実行される VM を管理するのは望ましくない場合。
* SQL Server または Windows Server のライセンスがない場合、または現在のライセンスを期限切れにする場合。

一連のシナリオに基づく各サービスの違いを次の表に示します。

| シナリオ | Azure VM の SQL Server | Azure SQL データベース |
|----------|-------------------------|--------------------|
| 移行 | データベースの最小限の変更が必要です。 | [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595) によって Azure SQL で利用できないと判断された機能を使用する場合や、ローカルにインストールされた実行可能ファイルなどの他の依存関係がある場合、データベースの変更が必要になることがあります。|
| 可用性、復旧、アップグレードの管理 | 可用性と復旧は手動で構成します。 アップグレードは、[VM Scale Sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) を使用して自動化できます。 | 自動的に管理されます。 |
| 基になる OS 構成 | 手動で構成します。 | 自動的に管理されます。 |
| データベース サイズの管理 | SQL Server インスタンスごとに最大 256 TB のストレージをサポートします。 | 行方向のパーティション分割が必要になるまでに 8 TB のストレージをサポートします。 |
| コストの管理 | SQL Server ライセンスのコスト、Windows Server ライセンスのコスト、VM のコスト (コア数、RAM、ストレージに基づく) を管理する必要があります。 | ([eDTU または DTU](/azure/sql-database/sql-database-what-is-a-dtu)、ストレージ、データベースの数 (エラスティック プールを使用している場合) に基づいて) サービス コストを管理する必要があります。 また、SLA のコストも管理する必要があります。 |

この 2 つの違いの詳細については、[Azure SQL での適切なデプロイ オプションの選択](/azure/sql-database/sql-database-paas-vs-sql-server-iaas)に関する記事を参照してください。

## <a name="faq"></a>よくあるご質問

* **SQL Server Management Studio や SQL Server Reporting Services (SSRS) などのツールは、Azure VM の SQL Server または Azure SQL Database で引き続き使用できますか?**

    はい。 Microsoft SQL ツールはすべてどちらのサービスでも機能します。 SSRS は Azure SQL Database には含まれていませんが、このツールを Azure VM で実行し、データベース インスタンスを参照することをお勧めします。

* **PaaS に移行したいのですが、データベースに互換性があるのかどうかがわかりません。役立つツールはありますか?**

    はい。 [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595) は、Azure SQL Database への移行の一環として使用されるツールです。 [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) は、IaaS または PaaS で使用できるプレビュー サービスです。

* **コストを見積もることはできますか?**

    はい。 [Azure 料金計算ツール](https://azure.microsoft.com/pricing/calculator/)を使用して、VM やデータベース サービスなど、すべての Azure サービスのコストを見積もることができます。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [適切な Azure ホスティング オプションの選択](choose.md)
