---
title: Azure Kubernetes Services での監視
description: Azure Kubernetes Services での監視
ms.date: 01/19/2021
ms.openlocfilehash: d044337150edddac9e24218ccaeaace1f413e654
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506033"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Azure Kubernetes Services での監視

Kubernetes の組み込みログはプリミティブです。 ただし、Kubernetes からログを取得し、適切に分析できる場所にするための優れたオプションがいくつかあります。 AKS クラスターを監視する必要がある場合は、Kubernetes のエラスティックスタックの構成が優れたソリューションです。

## <a name="azure-monitor-for-containers"></a>Azure Monitor for Containers

[コンテナーの Azure Monitor](/azure/azure-monitor/insights/container-insights-overview) は、Kubernetes だけでなく、DC/OS、Docker の群れ、Red Hat openshift などの他のオーケストレーションエンジンからのログの使用もサポートしています。

![さまざまなコンテナーからのログの消費 ](./media/containers-diagram.png)
 **図 7-10**。 さまざまなコンテナーからのログの使用

[Prometheus](https://prometheus.io/) は、広く普及しているオープンソースのメトリック監視ソリューションです。 クラウドネイティブコンピューティングファンデーションの一部です。 通常、Prometheus を使用するには、独自のストアで Prometheus サーバーを管理する必要があります。 ただし、 [コンテナーの Azure Monitor は、Prometheus メトリックエンドポイントと直接統合](/azure/azure-monitor/insights/container-insights-prometheus-integration)できるため、個別のサーバーは必要ありません。

ログとメトリックの情報は、クラスターで実行されているコンテナーだけでなく、クラスターからも収集されます。 これにより、2つのログ情報を相互に関連付けることができるため、エラーをより簡単に追跡できます。

ログコレクターのインストールは、 [Windows](/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) クラスターと [Linux](/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) クラスターで異なります。 ただし、どちらの場合も、ログの収集は Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)として実装されます。つまり、ログコレクターは各ノード上のコンテナーとして実行されます。

Azure Monitor デーモンを実行している orchestrator またはオペレーティングシステムにかかわらず、ログ情報は、ユーザーが使い慣れているのと同じ Azure Monitor ツールに転送されます。 この方法では、ハイブリッド Kubernetes/Azure Functions 環境などのさまざまなログソースが混在する環境で、並列操作を行うことができます。

![多数の実行中のコンテナーからのログ記録とメトリック情報を示すサンプルダッシュボードです。 ](./media/containers-dashboard.png)
**図 7-11**. 多数の実行中のコンテナーのログ記録とメトリック情報を示すサンプルダッシュボードです。

## <a name="logfinalize"></a>Log. Finalize ()

ログ記録は、大規模なアプリケーションのデプロイにおいて、見過ごされていて最も重要な部分の1つです。 アプリケーションのサイズと複雑さが増加するにつれて、アプリケーションのデバッグが困難になります。 高品質のログを使用すると、デバッグがはるかに簡単になり、"ほぼ不可能な" 領域から "快適なエクスペリエンス" に移行することができます。

>[!div class="step-by-step"]
>[前へ](logging-with-elastic-stack.md)
>[次へ](azure-monitor.md)
