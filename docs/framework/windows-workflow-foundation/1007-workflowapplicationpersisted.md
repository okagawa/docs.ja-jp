---
description: '詳細情報: 1007-WorkflowApplicationPersisted 化'
title: 1007 - WorkflowApplicationPersisted
ms.date: 03/30/2017
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
ms.openlocfilehash: 6598f4490d20f84abfc95223f9d5a3f4231b4754
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755578"
---
# <a name="1007---workflowapplicationpersisted"></a>1007 - WorkflowApplicationPersisted

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1007|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 ワークフロー アプリケーションが永続化されていることを示します。  
  
## <a name="message"></a>Message  

 WorkflowApplication ID: %1 が永続化されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|`xs:string`|ワークフロー アプリケーション ID|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
