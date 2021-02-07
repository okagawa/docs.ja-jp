---
description: 詳細については、「例外、トランザクション、および補正」を参照してください。
title: 例外、トランザクション、および補正
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: 3188b0238b1909847c289bb56274671ff4b307b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720190"
---
# <a name="exceptions-transactions-and-compensation"></a>例外、トランザクション、および補正

[!INCLUDE[wf1](../../../includes/wf1-md.md)] には、ワークフロー内のランタイム エラー条件を処理するさまざまな機構が用意されています。 ワークフローでは、例外ハンドラー、トランザクション、キャンセル、および補正の組み合わせを使用して、エラー条件の処理と適切な回復を行えます。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [例外](exceptions.md)  
 <xref:System.Activities.Statements.TryCatch> アクティビティを使用して、ワークフローで例外を処理する方法について説明します。  
  
 [トランザクション](workflow-transactions.md)  
 <xref:System.Activities.Statements.TransactionScope> アクティビティを利用してワークフローでトランザクションを使用する方法を説明します。  
  
 [補正](compensation.md)  
 ワークフローの補正について説明します。また、<xref:System.Activities.Statements.CompensableActivity>、<xref:System.Activities.Statements.Compensate>、および <xref:System.Activities.Statements.Confirm> などの補正アクティビティを使用する方法について説明します。  
  
 [キャンセル](modeling-cancellation-behavior-in-workflows.md)  
 組み込みのアクティビティとカスタム アクティビティを使用してワークフローでキャンセル処理を実行する方法について説明します。  
  
 [デバッグのワークフロー](debugging-workflows.md)  
 ワークフローをデバッグする方法について説明します。
