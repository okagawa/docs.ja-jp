---
description: '詳細情報: アクティビティライブラリ'
title: アクティビティ ライブラリ
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 7e59846d34b63683266fed2c4ec1ad4ed5cb9566
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792610"
---
# <a name="activity-library"></a>アクティビティ ライブラリ

このセクションには、Windows Workflow Foundation (WF) の高度なカスタムアクティビティを示すサンプルが含まれています。  
  
## <a name="in-this-section"></a>このセクションの内容

 [SendMail カスタム アクティビティ](sendmail-custom-activity.md)  
 <xref:System.Activities.AsyncCodeActivity> から派生するカスタム アクティビティを作成して、SMTP を使用して電子メールを送信し、ワークフロー アプリケーション内で使用する方法を示します。  
  
 [制限された並列 ForEach](throttled-parallel-foreach.md)  
 ph x="1" /&gt; アクティビティは、実行するコンカレンシー分岐の数を制限するためのコンカレンシー要因を設定できるという 1 つの例外を除き、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティと似ていることについて示します。
  
 [データベース アクセス アクティビティ](database-access-activities.md)  
 データベースにアクセスして情報を取得または変更し、 [ADO.NET](../../data/adonet/index.md) を使用してデータベースにアクセスできるようにするアクティビティを作成する方法を示します。  
  
 [.NET Framework 4.5 の外部化されたポリシー アクティビティ](externalized-policy-activity-in-net-framework-4-5.md)  
 ExternalizedPolicy4 アクティビティを使用して、 <xref:System.Workflow.Activities.Rules.RuleSet> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] wf 3.5 に付属するルールエンジンを使用して、(wf 4.5) の Windows Workflow Foundation の .NET Framework 3.5 (wf 3.5) オブジェクトの既存の Windows Workflow Foundation を直接実行する方法を示します。
  
 [非ジェネリックの ForEach](non-generic-foreach.md)  
 <xref:System.Activities.Statements.ForEach%601> アクティビティの非ジェネリック バージョンを作成する方法を示します。  
  
 [非ジェネリックの ParallelForEach](non-generic-parallelforeach.md)  
 <xref:System.Activities.Statements.ParallelForEach%601> アクティビティの非ジェネリック バージョンを作成する方法を示します。  
  
 [WorkflowInstanceId の取得](get-workflowinstanceid.md)  
 カスタム アクティビティ `GetWorkflowInstanceId` を使用して、ワークフロー インスタンス ID を返す方法を示します。
