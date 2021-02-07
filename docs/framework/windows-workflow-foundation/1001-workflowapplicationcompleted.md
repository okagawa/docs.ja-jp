---
description: '詳細情報: 1001-WorkflowApplicationCompleted'
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: d32028bbe582f4a1e31796ed1f75e41c651e6c59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755643"
---
# <a name="1001---workflowapplicationcompleted"></a>1001 - WorkflowApplicationCompleted

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1001|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 ワークフロー アプリケーションが Closed 状態で完了したことを示します。  
  
## <a name="message"></a>Message  

 WorkflowInstance ID: %1 は Closed 状態で完了しました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|ワークフローのインスタンス ID|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
