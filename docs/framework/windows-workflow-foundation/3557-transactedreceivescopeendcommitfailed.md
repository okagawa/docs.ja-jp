---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 4a4979047481687ef0d5c9d5891dec8f2826beed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263660"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a>3557 - TransactedReceiveScopeEndCommitFailed

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|3557|  
|Keywords|WFServices|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 CommittableTransaction の EndCommit への呼び出しが TransactionException をスローしたことを示します。  
  
## <a name="message"></a>Message  

 id = '%1' の CommittableTransaction に対する EndCommit への呼び出しにより、次のメッセージと共に TransactionException がスローされました: '%2'。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|TransactionId|xs:string|CommittableTransaction の ID。|  
|例外|xs:string|例外の詳細|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
