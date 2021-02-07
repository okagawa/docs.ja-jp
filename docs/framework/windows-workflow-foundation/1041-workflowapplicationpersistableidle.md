---
description: '詳細情報: 1041-WorkflowApplicationPersistableIdle'
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: eb004077a36ed3e78229df92a73972ed5feda665
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667760"
---
# <a name="1041---workflowapplicationpersistableidle"></a>1041 - WorkflowApplicationPersistableIdle

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1041|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 ワークフロー アプリケーションがアイドル状態のままであることを示します。 ワークフロー アプリケーションはアイドル状態または永続化されます。  
  
## <a name="message"></a>Message  

 WorkflowApplication Id: ' %1 ' はアイドル状態で、持続可能です。  次のアクションが実行されます: %2。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|xs:string|ワークフロー アプリケーション ID|  
|ActionTaken|xs:string|ワークフロー アプリケーションで実行されるアクション。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
