---
description: '詳細については、「方法: 非永続化インスタンスを照会する」を参照してください。'
title: '方法: 非永続的インスタンスを検索する'
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: 2cef64f97b32c5f1d31fa078200bc2fe15179485
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777659"
---
# <a name="how-to-query-for-non-persisted-instances"></a>方法: 非永続的インスタンスを検索する

サービスに SQL Workflow Instance Store の動作が定義されている場合、サービスの新しいインスタンスが作成されると、サービス ホストにより、そのサービス インスタンスの初期エントリがインスタンス ストアに作成されます。 その後、そのサービス インスタンスが初めて永続化されると、SQL Workflow Instance Store の動作により、現在のインスタンスの状態が、アクティベーション、回復、および制御に必要な追加データと共に格納されます。

インスタンスの初期エントリが作成された後にインスタンスが永続化されていない場合、そのサービス インスタンスの状態を非永続的状態と呼びます。 永続的サービス インスタンスはすべてクエリおよび制御できますが、 非永続的サービス インスタンスはクエリも制御もできません。 非永続的インスタンスが未処理の例外によって中断された場合は、クエリはできますが制御はできません。

次のような場合、まだ永続化されていない永続性サービス インスタンスが非永続的状態のままになります。

- インスタンスが初めて永続化される前にサービス ホストがクラッシュした場合。 インスタンスの初期エントリがインスタンス ストアに残ります。 インスタンスを回復することはできません。 関連付けられるメッセージが受信されると、インスタンスが再びアクティブになります。

- インスタンスが初めて永続化される前にインスタンスで未処理の例外が発生した場合。 次の状況が発生します。

  - **Unhandledexceptionaction** プロパティの値が "**破棄**" に設定されている場合は、サービスの配置情報がインスタンスストアに書き込まれ、インスタンスがメモリからアンロードされます。 インスタンスは、非永続的状態のまま永続性データベースに残ります。

  - **Unhandledexceptionaction** プロパティの値が **AbandonAndSuspend** に設定されている場合、サービスの配置情報は永続性データベースに書き込まれ、インスタンスの状態は "**中断**" に設定されます。 インスタンスを再開、取り消し、または終了することはできません。 インスタンスはまだ永続化されておらず、インスタンスのデータベース エントリが完成していないため、サービス ホストはインスタンスを読み込むことができません。

  - **Unhandledexceptionaction** プロパティの値が **Cancel** または **Terminate** に設定されている場合は、サービスのデプロイ情報がインスタンスストアに書き込まれ、インスタンスの状態が **Completed** に設定されます。

以降では、SQL 永続性データベースで非永続的インスタンスを検索するためのサンプル クエリと、それらのインスタンスをデータベースから削除するためのサンプル クエリを紹介します。

## <a name="to-find-all-instances-not-persisted-yet"></a>まだ永続化されていないインスタンスをすべて検索するには

次の SQL クエリは、まだ永続性データベースに永続化されていないすべてのインスタンスの ID と作成時刻を返します。

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;
```

## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a>まだ永続化されておらず、読み込まれてもいないインスタンスをすべて検索するには

 次の SQL クエリは、まだ永続化されておらず、読み込まれてもいないすべてのインスタンスの ID と作成時刻を返します。

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;
```

## <a name="to-find-all-suspended-instances-not-persisted-yet"></a>まだ永続化されていない中断されたインスタンスをすべて検索するには

次の SQL クエリは、まだ永続化されていない中断状態のすべてのインスタンスの ID、作成時刻、中断の理由、および中断例外の名前を返します。

```sql
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;
```

## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a>非永続的インスタンスを永続性データベースから削除するには

非永続的インスタンスがないかどうかをインスタンス ストアで定期的に確認して、関連付けられるメッセージをもう受信しないことがわかっている場合は、インスタンス ストアから削除する必要があります。 たとえば、数か月にわたってデータベースに残っているインスタンスがある場合、そのワークフローの通常の有効期間が数日程度なら、クラッシュした未初期化のインスタンスと見なしても問題ありません。

一般に、非永続的インスタンスは、中断されていない場合や読み込まれていない場合は安全に削除できます。 このインスタンスセットには、作成したばかりでまだ永続化されていないインスタンスが含まれているため、永続化されていない **すべて** のインスタンスを削除しないでください。 削除する必要があるのは、インスタンスを読み込んだワークフロー サービス ホストで例外が発生したり、インスタンス自体で例外が発生したりしたために永続化されずに残っているインスタンスだけです。

> [!WARNING]
> 非永続的インスタンスをインスタンス ストアから削除すると、ストアのサイズが小さくなって、ストア操作のパフォーマンスが向上する可能性があります。
