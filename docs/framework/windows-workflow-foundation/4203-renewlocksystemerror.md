---
description: '詳細情報: 4203-RenewLockSystemError'
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 0e62c501391fcaec56f2016631707832170775ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792779"
---
# <a name="4203---renewlocksystemerror"></a>4203 - RenewLockSystemError

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|4203|  
|Keywords|WFInstanceStore|  
|Level|エラー|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 ロックの有効期限が既に過ぎているか、またはロック所有者が削除されたために、SQL プロバイダーはロックの有効期限を延長できなかったことを示します。 SqlWorkflowInstanceStore は中止されます。  
  
## <a name="message"></a>Message  

 ロックの有効期限を延長できませんでした。ロックの有効期限が既に過ぎているか、ロックの所有者が削除されました。 SqlWorkflowInstanceStore を中止します。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
