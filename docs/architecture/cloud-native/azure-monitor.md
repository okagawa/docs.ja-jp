---
title: Azure Monitor
description: Azure Monitor を使用すると、システムが実行されていることを確認できます。
ms.date: 01/19/2021
ms.openlocfilehash: a93b71db642e05a830b20b80d8387c24d35ea8c1
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506176"
---
# <a name="azure-monitor"></a>Azure Monitor

他のクラウドプロバイダーは、Azure で見つかったクラウドアプリケーション監視ソリューションよりも成熟していません。 Azure Monitor は、システムの状態を表示できるように設計されたツールのコレクションの包括的な名前です。 クラウドネイティブサービスがどのように実行されているかを理解し、それらに影響する問題を事前に特定するのに役立ちます。 図7-12 に、Azure Monitor の高レベルのビューを示します。

![Azure Monitor の概要を表示します。 ](./media/azure-monitor.png)
**図 7-12**. Azure Monitor の概要を表示します。

## <a name="gathering-logs-and-metrics"></a>ログとメトリックの収集

監視ソリューションの最初の手順は、可能な限り多くのデータを収集することです。 収集されるデータが多いほど、詳細な洞察が得られます。 従来、システムのインストルメント化は困難でした。 Simple Network Management Protocol (SNMP) は、マシンレベル情報を収集するための gold 標準プロトコルでしたが、多くの知識と構成を必要としていました。 幸いにも、最も一般的なメトリックは Azure Monitor によって自動的に収集されるため、このようなハード作業の大部分は排除されています。

アプリケーションレベルのメトリックとイベントは、デプロイされるアプリケーションに固有のものであるため、自動的にインストルメント化することはできません。 これらのメトリックを収集するために、顧客が注文にサインアップまたは完了したときなど、このような情報を直接報告するための [sdk と api](/azure/azure-monitor/app/api-custom-events-metrics) が用意されています。 例外をキャプチャして、Application Insights 経由で Azure Monitor に返すこともできます。 Sdk は、ゴー、Python、JavaScript、.NET 言語などのクラウドネイティブアプリケーションで検出されたほとんどすべての言語をサポートしています。

アプリケーションの状態に関する情報を収集する最終的な目標は、エンドユーザーのエクスペリエンスを向上させることです。 ユーザーが [外部の web テストを](/azure/azure-monitor/app/monitor-web-app-availability)実行する場合よりも問題が発生しているかどうかを確認するには、どうすればよいでしょうか。 これらのテストは、世界中の場所から web サイトに ping を実行したり、エージェントがサイトにログインしてユーザーの操作をシミュレートしたりするのと同じように簡単に行うことができます。

## <a name="reporting-data"></a>レポートデータ

データが収集されると、データの操作、要約、およびグラフへのプロットが可能になり、問題が発生したときにすぐにユーザーが表示できるようになります。 これらのグラフは、システムのいくつかの側面についてストーリーを示すために設計された複数ページのレポートである、ダッシュボードまたはブックに収集できます。

人工知能や機械学習を行わずに、最新のアプリケーションを完成させることはできません。 このため、Azure のさまざまな machine learning ツールにデータを [渡すことが](https://www.youtube.com/watch?v=Cuza-I1g9tw) できるため、表示されない傾向や情報を抽出できます。

Application Insights には、 *Kusto* と呼ばれる強力な (SQL に似た) クエリ言語が用意されています。これにより、レコードのクエリ、集計、グラフのプロットを行うことができます。 たとえば、次のクエリでは、2007年11月のすべてのレコードを検索し、州別にグループ化し、上位10を円グラフとしてプロットします。

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

図7-13 は、この Application Insights クエリの結果を示しています。

![クエリ結果の Application Insights ](./media/application_insights_example.png)
 **図 7-13**。 クエリ結果を Application Insights します。

[Kusto クエリを試すためのプレイグラウンド](https://dataexplorer.azure.com/clusters/help/databases/Samples)があります。 [サンプルクエリ](/azure/kusto/query/samples)の読み取りも参考になる場合があります。

## <a name="dashboards"></a>ダッシュボード

Azure Monitor から情報を表示するために使用できる、いくつかの異なるダッシュボードテクノロジがあります。 単純に、Application Insights でクエリを実行し、 [データをグラフにプロット](/azure/azure-monitor/learn/tutorial-app-dashboards)するだけです。

![メインの Azure ダッシュボード図7-14 に埋め込まれている Application Insights のグラフの例を次に示し ](./media/azure_dashboard.png)
 ます。 メインの Azure ダッシュボードに埋め込まれている Application Insights グラフの例を示します。

これらのグラフは、ダッシュボード機能を使用して適切に Azure portal に埋め込むことができます。 複数の層のデータにドリルダウンできるなど、より厳しい要件を持つユーザーには、Azure Monitor データを [Power BI](https://powerbi.microsoft.com/)できます。 Power BI は、業界をリードするエンタープライズクラスのビジネスインテリジェンスツールであり、さまざまなデータソースからデータを集計できます。

![ダッシュボードの Power BI 例](./media/powerbidashboard.png)

**図 7-15**。 ダッシュボード Power BI 例。

## <a name="alerts"></a>警告

データダッシュボードが不十分な場合もあります。 ダッシュボードの監視が開始されていない場合でも、問題が解決されるまで、または検出されるまでに数時間かかることがあります。 このため、Azure Monitor には、上位ノッチの [アラートソリューション](/azure/azure-monitor/platform/alerts-overview)も用意されています。 アラートは、次のような幅広い条件によってトリガーできます。

- メトリックの値
- ログの検索クエリ
- アクティビティ ログのイベント
- 基になっている Azure プラットフォームの正常性
- Web サイトの可用性のテスト

トリガーされると、アラートはさまざまなタスクを実行できます。 単純な側では、アラートは電子メールによる通知をメーリングリストまたはテキストメッセージに送信するだけです。 さらに関連するアラートによって、PagerDuty などのツールでワークフローがトリガーされることがあります。これは、特定のアプリケーションの呼び出し元を認識します。 アラートは、ワークフローのほぼ無制限の可能性を [Microsoft Flow](https://flow.microsoft.com/) にロックを解除するアクションをトリガーできます。

アラートの一般的な原因を特定すると、アラートの原因と解決方法についての詳細情報を使用してアラートを強化できます。 クラウドネイティブアプリケーションの高成熟した展開では、障害が発生したノードをスケールセットから削除する、または自動スケールアクティビティをトリガーするなどの操作を実行する自己復旧タスクを開始することを選択できます。 最終的には、午前2時に勤務先の担当者をウェイクアップして、ライブサイトの問題を解決する必要がなくなる可能性があります。システムは、翌朝に仕事が到着するまで、補償または少なくとも limp を調整できるようにするためです。

Azure Monitor は、自動的に機械学習を活用して、デプロイされたアプリケーションの通常の動作パラメーターを把握します。 この方法では、通常のパラメーターの外部で動作しているサービスを検出できます。 たとえば、サイトでの一般的な平日のトラフィックは、1分あたり1万の要求になることがあります。 その後、特定の週に、要求の数が突然、1分あたりの非常に異常な2万要求に達します。 [スマート検出](/azure/azure-monitor/app/proactive-diagnostics) では、この偏差が基準からのものであることがわかり、アラートがトリガーされます。 同時に、傾向分析は、トラフィックの負荷が予想されるときに偽陽性が発生しないようにするのに十分なスマートです。

## <a name="references"></a>リファレンス

- [Azure Monitor](/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[前へ](monitoring-azure-kubernetes.md)
>[次へ](identity.md)
