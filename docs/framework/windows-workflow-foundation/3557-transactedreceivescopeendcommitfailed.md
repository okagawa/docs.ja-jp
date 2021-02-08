---
description: '詳細情報: 3557-TransactedReceiveScopeEndCommitFailed'
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 7865ae27e7ce5b3f13b3567f3f8aeebd6edf3fd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777984"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a>3557 - TransactedReceiveScopeEndCommitFailed

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|3557|  
|Keywords|WFServices|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 CommittableTransaction の EndCommit への呼び出しが TransactionException をスローしたことを示します。  
  
## <a name="message"></a>Message  

 id = '%1' の CommittableTransaction に対する EndCommit への呼び出しにより、次のメッセージと共に TransactionException がスローされました: '%2'。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|TransactionId|xs:string|CommittableTransaction の ID。|  
|例外|xs:string|例外の詳細|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
