---
description: '詳細情報: WF でのトランザクションアクティビティ'
title: WF におけるトランザクションのアクティビティ
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: f088c586998d3dbec8b94dcf0f02603a68b55a40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755136"
---
# <a name="transaction-activities-in-wf"></a>WF におけるトランザクションのアクティビティ

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、トランザクションや、補正、取り消しをモデル化するためのシステム指定のアクティビティがいくつかあります。 これらのプログラミング モデルにより、ビジネス ロジックとエラー処理の変更の場合に、ワークフローは進行を続けることができます。 トランザクション、補正、およびキャンセルの詳細については、「 [トランザクション](workflow-transactions.md)、 [補正](compensation.md)、および [キャンセル](modeling-cancellation-behavior-in-workflows.md)」を参照してください。  
  
## <a name="transaction-activities"></a>トランザクションのアクティビティ  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|アクティビティの形式のキャンセル ロジックを、アクティビティとしても表される実行のメイン パスに関連付けます。|  
|<xref:System.Activities.Statements.CompensableActivity>|子アクティビティの補正をサポートします。|  
|<xref:System.Activities.Statements.Compensate>|<xref:System.Activities.Statements.CompensableActivity> の補正ハンドラーを明示的に呼び出します。|  
|<xref:System.Activities.Statements.Confirm>|<xref:System.Activities.Statements.CompensableActivity> の確認ハンドラーを明示的に呼び出します。|  
|<xref:System.Activities.Statements.TransactionScope>|トランザクションの境界を設定します。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|受信したメッセージによって開始されるトランザクションの有効期間のスコープを設定します。 トランザクションは、開始メッセージでワークフローにフローすることも、メッセージの受信時にディスパッチャーが作成することも可能です。 **注:** は、 <xref:System.ServiceModel.Activities.TransactedReceiveScope> **ツールボックス** の [**メッセージング**] セクションにあります。|
