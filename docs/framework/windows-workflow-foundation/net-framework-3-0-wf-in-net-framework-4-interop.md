---
description: 詳細については、「.NET Framework 4 での .NET Framework 3.0 WF 活動と Interop アクティビティの使用」を参照してください。
title: Interop アクティビティと .NET Framework 4 内の .NET Framework 3.0 WF アクティビティの使用
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: 8a91e9488b9885682d2d46f7b6afd512700157d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720112"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Interop アクティビティと .NET Framework 4 内の .NET Framework 3.0 WF アクティビティの使用

<xref:System.Activities.Statements.Interop>アクティビティは、 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ワークフロー内の .NET Framework 3.5 (wf 3.5) アクティビティをラップする (wf 4.5) アクティビティです [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 。 WF 3 アクティビティは、単一のリーフ アクティビティまたはツリー全体のアクティビティです。 実行 (キャンセルと例外処理を含む) と .NET Framework 3.5 アクティビティの永続化は、実行中のワークフローインスタンスのコンテキスト内で発生し [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ます。  
  
> [!NOTE]
> <xref:System.Activities.Statements.Interop>ワークフローのプロジェクトで [**ターゲットフレームワーク**] の設定が [ **.NET Framework 4.5**] に設定されていない限り、アクティビティはワークフローデザイナーツールボックスに表示されません。  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>WF 3 アクティビティと Interop アクティビティを使用するための基準  

 <xref:System.Activities.Statements.Interop> アクティビティ内で WF 3 アクティビティを正常に実行するには、次の基準を満たす必要があります。  
  
- WF 3 アクティビティが <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType> から派生しています。  
  
- WF 3 アクティビティが `public` として宣言されています。また、`abstract` ではありません。  
  
- WF 3 アクティビティには、パラメーターなしのパブリックコンストラクターが必要です。  
  
- <xref:System.Activities.Statements.Interop> アクティビティがサポートできるインターフェイス型にある制限のため、<xref:System.Workflow.Activities.HandleExternalEventActivity> と <xref:System.Workflow.Activities.CallExternalMethodActivity> は直接使用できませんが、ワークフロー通信アクティビティ ツール (WCA.exe) を使用して作成される派生アクティビティを使用できます。 詳細については、 [Windows Workflow Foundation ツール](/previous-versions/dotnet/netframework-3.5/ms734408(v=vs.90)) を参照してください。  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Interop アクティビティ内の WF 3 アクティビティの構成  

 データを構成して、相互運用上の境界にまたがって WF 3 アクティビティとの間でやり取りするには、WF 3 アクティビティのプロパティとメタデータのプロパティを <xref:System.Activities.Statements.Interop> アクティビティで公開します。 WF 3 アクティビティのメタデータのプロパティ (<xref:System.Workflow.ComponentModel.Activity.Name%2A> など) は、<xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> コレクションを介して公開されます。 これは、WF 3 アクティビティのメタデータのプロパティに関する値を定義するために使用される名前と値ペアのコレクションです。 メタデータのプロパティは、<xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> フラグを設定する依存関係プロパティに基づくプロパティです。  
  
 WF 3 アクティビティのプロパティは、<xref:System.Activities.Statements.Interop.ActivityProperties%2A> コレクションを介して公開されます。 これは名前と値ペアのセットです。この各値は <xref:System.Activities.Argument> オブジェクトで、WF 3 アクティビティのプロパティの引数を定義するために使用されます。 WF 3 アクティビティプロパティの方向は推論できないため、すべてのプロパティがペアとして表示され <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> ます。 アクティビティによるプロパティの使用方法によっては、<xref:System.Activities.InArgument> エントリ、<xref:System.Activities.OutArgument> エントリ、またはその両方を提供できます。 コレクションに含まれる <xref:System.Activities.InArgument> エントリの想定される名前は、WF 3 アクティビティに定義されているプロパティの名前です。 コレクション内のエントリの予想される名前 <xref:System.Activities.OutArgument> は、プロパティの名前と文字列 "Out" を連結したものです。  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Interop アクティビティ内で WF 3 アクティビティを使用する際の制限  

 WF 3 システム標準アクティビティは、<xref:System.Activities.Statements.Interop> アクティビティで直接ラップすることはできません。 <xref:System.Workflow.Activities.DelayActivity> などの一部の WF 3 アクティビティの場合、これは類似する WF 4.5 アクティビティがあることが原因です。 その他のアクティビティの場合、これはそのアクティビティの機能がサポートされないことが原因です。 多くの WF 3 システム標準アクティビティは、次の制限に従い、<xref:System.Activities.Statements.Interop> アクティビティによってラップしたワークフロー内で使用できます。  
  
1. <xref:System.ServiceModel.Activities.Send> アクティビティでは、<xref:System.ServiceModel.Activities.Receive> および <xref:System.Activities.Statements.Interop> を使用できません。  
  
2. <xref:System.Workflow.Activities.WebServiceInputActivity> 内では、<xref:System.Workflow.Activities.WebServiceOutputActivity>、<xref:System.Workflow.Activities.WebServiceFaultActivity>、および <xref:System.Activities.Statements.Interop> を使用できません。  
  
3. <xref:System.Workflow.Activities.InvokeWorkflowActivity> アクティビティでは、<xref:System.Activities.Statements.Interop> を使用できません。  
  
4. <xref:System.Workflow.ComponentModel.SuspendActivity> アクティビティでは、<xref:System.Activities.Statements.Interop> を使用できません。  
  
5. <xref:System.Activities.Statements.Interop> アクティビティ内では、補正関係のアクティビティを使用できません。  
  
 また、<xref:System.Activities.Statements.Interop> アクティビティ内での WF 3 アクティビティの使用に関して理解できる動作仕様もいくつかあります。  
  
1. <xref:System.Activities.Statements.Interop> アクティビティ内に含まれる WF 3 アクティビティは、<xref:System.Activities.Statements.Interop> アクティビティを実行するときに初期化されます。 WF 4.5 には、実行前にワークフロー インスタンスの初期化フェーズはありません。  
  
2. WF 4.5 ランタイムは、トランザクションの開始場所 (<xref:System.Activities.Statements.Interop> アクティビティ内かどうか) を問わず、トランザクションの開始時にワークフロー インスタンスの状態を確認しません。  
  
3. <xref:System.Activities.Statements.Interop> アクティビティ内のアクティビティに関する WF 3 追跡レコードは、WF 4.5 の追跡参加要素に <xref:System.Activities.Tracking.InteropTrackingRecord> オブジェクトとして提供されます。 <xref:System.Activities.Tracking.InteropTrackingRecord> は <xref:System.Activities.Tracking.CustomTrackingRecord> の派生物です。  
  
4. WF 3 カスタム アクティビティからは、WF 3 ワークフロー ランタイム内とまったく同じ方法で、相互運用環境内でワークフロー キューを使用してデータにアクセスできます。 カスタム アクティビティ コードの変更は必要ありません。 ホストでは、<xref:System.Activities.Bookmark> を再開することで WF 3 ワークフロー キューにデータが追加されます。 ブックマークの名前は、<xref:System.IComparable> ワークフロー キュー名の文字列の形式です。
