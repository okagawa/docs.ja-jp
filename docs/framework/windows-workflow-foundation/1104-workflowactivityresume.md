---
description: '詳細情報: 1104-WorkflowActivityResume'
title: 1104 - WorkflowActivityResume
ms.date: 03/30/2017
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
ms.openlocfilehash: 875bbae9bdfd772cc9156cf544b7069d8d0b791f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667500"
---
# <a name="1104---workflowactivityresume"></a>1104 - WorkflowActivityResume

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1104|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 ワークフロー アクティビティが再開されたことを示します。  
  
## <a name="message"></a>Message  

 WorkflowInstance ID: '%1' E2E アクティビティ  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:string|ワークフロー インスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
