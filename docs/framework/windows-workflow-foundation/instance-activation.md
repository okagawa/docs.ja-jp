---
description: '詳細情報: インスタンスのアクティブ化'
title: インスタンスのアクティブ化処理
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: a301f49fb79e7c74cd3a64e891526e5b89fdd1c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631204"
---
# <a name="instance-activation"></a>インスタンスのアクティブ化処理

SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、実行可能またはアクティブ化可能なワークフロー インスタンスを永続性データベースで検出します。 このタスクは、実行可能なワークフロー インスタンスを検出すると、このインスタンスをアクティブ化することができるワークフロー ホストに通知します。 Instance Store がアクティブ化可能なワークフロー インスタンスを検出した場合、ワークフロー ホストをアクティブ化する汎用ホストに Instance Store が通知を行い、ワークフロー ホストがワークフロー インスタンスを実行します。 このトピックの以降のセクションでは、インスタンスのアクティブ化処理を詳細に説明します。  
  
## <a name="detecting-and-activating-runnable-workflow-instances"></a><a name="RunnableSection"></a> 実行可能なワークフローインスタンスの検出とアクティブ化  

 SQL Workflow Instance Store では、インスタンスが中断状態または完了状態ではなく、次の条件を満たす場合に、ワークフローインスタンスが実行可能 *であると* 見なされます。  
  
- インスタンスがロック解除されていて、保留タイマーの期限が切れている。  
  
- インスタンスに期限切れのロックがある。  
  
- インスタンスのロックが解除され、状態が [ **実行中**] になります。  
  
 SQL Workflow Instance Store は、実行可能なインスタンスを見つけると <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> を生成します。 その後、SqlWorkflowInstanceStore は <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> がストアで一度呼び出されるまで監視を停止します。  
  
 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> に定期受信し、インスタンスの読み込みが可能なワークフロー ホストは、インスタンス ストアに対して <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> を実行してインスタンスをメモリに読み込みます。 ホストとインスタンスのメタデータプロパティ **Workflowservicetype** が同じ値に設定されている場合、ワークフローホストはワークフローインスタンスを読み込むことができると見なされます。  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>アクティブ化可能なワークフロー インスタンスの検出とアクティブ化  

 インスタンスが実行可能で、インスタンスを読み込むことができるワークフローホストがコンピューター上で実行されていない場合、ワークフローインスタンスは *アクティブ* 化可能と見なされます。 実行可能なワークフロー インスタンスの定義については、前の「実行可能なワークフロー インスタンスの検出とアクティブ化」を参照してください。  
  
 SQL Workflow Instance Store は、データベースでアクティブ化可能なワークフロー インスタンスを見つけると <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> を生成します。 その後、SqlWorkflowInstanceStore は <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> がストアで一度呼び出されるまで監視を停止します。  
  
 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> に定期受信している汎用ホストは、イベントを受け取ると、インスタンス ストアに対して <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> を実行して、ワークフロー ホストの作成に必要なアクティブ化のパラメーターを取得します。 汎用ホストは、このアクティブ化パラメーターを使用してワークフロー ホストを作成します。作成されたワークフロー ホストは、実行可能なサービス インスタンスを読み込んで実行します。  
  
## <a name="generic-hosts"></a>汎用ホスト  

 汎用ホストは、"メタデータ" プロパティの値を持つホストで、汎用ホストの **workflowservicetype** が workflowservicetype に設定されてい **ます。任意** のワークフロー型を処理できることを示します。 汎用ホストには、 **ActivationType** という名前の XName パラメーターがあります。  
  
 現在、SQL Workflow Instance Store は、ActivationType パラメーターの値が WAS に設定 **さ** れた汎用ホストをサポートしています。 ActivationType が WAS に設定されていない場合、SQL Workflow Instance Store は <xref:System.Runtime.DurableInstancing.InstancePersistenceException> をスローします。 Windows Server AppFabric のホスト機能に付属するワークフロー管理サービスは、アクティブ化の種類が **WAS** に設定された汎用ホストです。  
  
 WAS アクティブ化の場合、汎用ホストは、新しいホストをアクティブ化できるエンドポイント アドレスを派生する一連のアクティブ化パラメーターを要求します。 WAS アクティブ化のアクティブ化パラメーターは、サイトの名前、サイトを基準としたアプリケーションの相対パス、アプリケーションを基準としたサービスの相対パスです。 SQL Workflow Instance Store は、<xref:System.Activities.DurableInstancing.SaveWorkflowCommand> の実行中にこれらのアクティブ化パラメーターを格納します。  
  
## <a name="runnable-instances-detection-period"></a>実行可能インスタンス検出期間  

 SQL Workflow Instance Store の "実行可能 **インスタンス検出期間** " プロパティは、前の検出サイクルの後に、Sql Workflow instance store が永続性データベースで実行可能またはアクティブ化可能なワークフローインスタンスを検出する検出タスクを実行するまでの期間を指定します。 このプロパティの詳細については、「実行可能 [インスタンスの検出期間](runnable-instances-detection-period.md) 」を参照してください。
