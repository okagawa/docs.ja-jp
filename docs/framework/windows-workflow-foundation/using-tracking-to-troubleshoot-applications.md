---
description: '詳細情報: 追跡を使用したアプリケーションのトラブルシューティング'
title: 追跡を使用したアプリケーションのトラブルシューティング
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: 9ff2c1b9a4a35a75a9f4d2229b5b43d6607e7557
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754993"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>追跡を使用したアプリケーションのトラブルシューティング

Windows Workflow Foundation (WF) を使用すると、ワークフロー関連の情報を追跡して、Windows Workflow Foundation アプリケーションまたはサービスの実行に詳細を提供できます。 Windows Workflow Foundation ホストは、ワークフローインスタンスの実行中にワークフローイベントをキャプチャできます。 ワークフローによってエラーまたは例外が生成された場合は、Windows Workflow Foundation 追跡の詳細を使用して、処理のトラブルシューティングを行うことができます。  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>WF の追跡を使用した WF のトラブルシューティング  

 Windows Workflow Foundation アクティビティの処理中に発生したエラーを検出するには、状態が Faulted であるを照会する追跡プロファイルを使用して追跡を有効にすることができ <xref:System.Activities.Tracking.ActivityStateRecord> ます。 対応するクエリは、次のコードで指定されています。  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 エラーがエラー ハンドラー (<xref:System.Activities.Statements.TryCatch> アクティビティなど) 内で反映および処理される場合、<xref:System.Activities.Tracking.FaultPropagationRecord> を使用して検出できます。 <xref:System.Activities.Tracking.FaultPropagationRecord> は、エラーのソース アクティビティとエラー ハンドラーの名前を示します。 には、エラー <xref:System.Activities.Tracking.FaultPropagationRecord> の例外スタックの形式でエラーの詳細が含まれています。 をサブスクライブするためのクエリを <xref:System.Activities.Tracking.FaultPropagationRecord> 次の例に示します。  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 エラーがワークフロー内で処理されない場合は、ワークフロー インスタンスでハンドルされない例外になり、ワークフロー インスタンスは中止されます。 ハンドルされない例外の詳細を把握するために、追跡プロファイルでは、次のように `state name="UnhandledException"` を持つワークフロー インスタンス レコードを照会する必要があります。  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 ワークフローインスタンスでハンドルされない例外が発生した場合、 <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> Windows Workflow Foundation の追跡が有効になっていると、オブジェクトが生成されます。  
  
 この追跡レコードには、例外スタックの形式でエラーの詳細が含まれます。 これには、エラーの原因となったエラー (アクティビティなど) の詳細が含まれており、未処理の例外が発生しています。Windows Workflow Foundation からのエラーイベントをサブスクライブするには、追跡参加要素を追加して追跡を有効にします。 この参加要素は、`ActivityStateQuery (state="Faulted")`、<xref:System.Activities.Tracking.FaultPropagationRecord>、および `WorkflowInstanceQuery (state="UnhandledException")` を照会する追跡プロファイルで構成します。  
  
 ETW 追跡参加要素を使用して追跡を有効にした場合、エラー イベントは ETW セッションに書き出されます。 イベントはイベント ビューアーを使用して表示できます。 これは、分析チャネルの [ **イベントビューアー] >[アプリケーションとサービスログ]->[Microsoft >Windows->アプリケーションサーバー-アプリケーション** ] の下にあります。  
  
## <a name="see-also"></a>関連項目

- [Windows Server App Fabric の監視](/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric を使用したアプリケーションの監視](/previous-versions/appfabric/ee677276(v=azure.10))
