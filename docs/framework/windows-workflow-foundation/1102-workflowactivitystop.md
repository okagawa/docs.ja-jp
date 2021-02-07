---
description: '詳細情報: 1102-WorkflowActivityStop'
title: 1102 - WorkflowActivityStop
ms.date: 03/30/2017
ms.assetid: 285e5cb8-e90d-4914-ac06-e9b176ffefa2
ms.openlocfilehash: 726af6a79058e93a066e0f486d7cf5be1ef8e4be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667578"
---
# <a name="1102---workflowactivitystop"></a>1102 - WorkflowActivityStop

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1102|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 ワークフロー アクティビティが中止されたことを示します。  
  
## <a name="message"></a>Message  

 WorkflowInstance ID: '%1' E2E アクティビティ  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:string|ワークフロー インスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
