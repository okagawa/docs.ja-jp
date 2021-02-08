---
description: 永続化されていないワークフローインスタンスについての詳細情報
title: 非永続化ワークフロー インスタンス
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 0ee5968426a6bb800b9e70ac592c6da191c22511
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787904"
---
# <a name="non-persisted-workflow-instances"></a>非永続化ワークフロー インスタンス

状態が永続するワークフローの新しいインスタンスを <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> に作成すると、サービス ホストはそのサービスのエントリをインスタンス ストアに作成します。 その後、ワークフロー インスタンスが初めて永続化されると、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> は現在のインスタンス状態を格納します。 ワークフローが Windows プロセス アクティブ化サービスにホストされている場合は、インスタンスが初めて永続化するとサービス配置データもインスタンス ストアに書き込まれます。

ワークフローインスタンスが永続化されていない限り、 **永続化** されていない状態になります。 この状態の場合、アプリケーション ドメインのリサイクル、ホストの障害、またはコンピューターの障害の後にワークフロー インスタンスを回復することはできません。

## <a name="the-non-persisted-state"></a>非永続化状態

次のような場合、まだ永続化されていない永続性ワークフロー インスタンスが非永続的状態のままになります。

- ワークフロー インスタンスが初めて永続化される前にサービス ホストがクラッシュした場合。 ワークフロー インスタンスはインスタンス ストアに残り、回復されません。 関連付けられるメッセージが受信されると、ワークフロー インスタンスが再びアクティブになります。

- ワークフロー インスタンスが初めて永続化される前にインスタンスで例外が発生した場合。 返される <xref:System.Activities.UnhandledExceptionAction> に応じて、次のシナリオが発生します。

  - <xref:System.Activities.UnhandledExceptionAction> が <xref:System.Activities.UnhandledExceptionAction.Abort> に設定されている場合:  例外が発生すると、サービス配置情報がインスタンス ストアに書き込まれ、ワークフロー インスタンスがメモリからアンロードされます。 ワークフロー インスタンスは非永続化状態となり、再読み込みできません。

  - <xref:System.Activities.UnhandledExceptionAction> が <xref:System.Activities.UnhandledExceptionAction.Cancel> または <xref:System.Activities.UnhandledExceptionAction.Terminate> に設定されている場合:  例外が発生すると、サービス配置情報がインスタンス ストアに書き込まれ、アクティビティ インスタンスの状態が <xref:System.Activities.ActivityInstanceState.Closed> に設定されます。

アンロードされている非永続化ワークフロー インスタンスが発生するリスクを最低限に抑えるため、ライフサイクルの早い段階でワークフローを永続化することをお勧めします。

## <a name="detection-and-removal-of-non-persisted-instances"></a>非永続化インスタンスの検出と削除

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> は非永続化ワークフロー インスタンスをインスタンス ストアから削除しません。 非永続化ワークフロー インスタンスが関連付けられている期限切れのロックの所有者も削除されません。

管理者は定期的にインスタンス ストアの非永続化インスタンスを調べることをお勧めします。 管理者はこのワークフローが相関メッセージを受信しないことがわかっている限り、これらのインスタンスをインスタンス ストアから削除することができます。 たとえば、数か月にわたってデータベースに残っているインスタンスがある場合、そのワークフローの通常の有効期間が数日程度なら、クラッシュした初期化済みのインスタンスと見なしても問題ありません。

SQL Workflow Instance Store 内の非永続化インスタンスを見つけるには、次の SQL クエリを使用できます。

- このクエリは、まだ永続化されていないすべてのインスタンスを検索し、その ID と作成時刻 (UTC 時刻で格納) を返します。

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
  ```

- このクエリは、まだ永続化されておらず、読み込まれてもいないすべてのインスタンスを検索し、その ID と作成時刻 (UTC 時刻で格納) を返します。

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and CurrentMachine is NULL
  ```

- このクエリは、まだ永続化されていない中断されたすべてのインスタンスを検索し、その ID、作成時刻 (UTC 時刻で格納)、中断の理由、およびその例外名を返します。

  ```sql
  select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and IsSuspended = 1
  ```

非永続化インスタンスを削除する際は注意してください。 一般に、<xref:System.ServiceModel.Activities.WorkflowServiceHost> によって作成された非永続化インスタンスは、中断されている場合や読み込まれていない場合は安全に削除できます。 これらの特定のインスタンスは、次の SQL コマンドを正しいインスタンス ID に置き換えて使用し、`[System.Activities.DurableInstancing].[Instances]` ビューから削除することで、ストアから削除することが可能です。

```sql
delete [System.Activities.DurableInstancing].[Instances]
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’
```

> [!WARNING]
> 作成されたばかりでまだ永続化されていないインスタンスもあるため、非永続的インスタンスをすべて削除することはお勧めしません。
