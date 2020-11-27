---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: a192ffe19777ca3e2e9784f6506a0c2929ced000
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275532"
---
# <a name="1016---completecompletionworkitem"></a>1016 - CompleteCompletionWorkItem

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1016|  
|Keywords|WFRuntime|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 CompletionWorkItem が完了したことを示します。  
  
## <a name="message"></a>Message  

 親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem が完了しました。 Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|親アクティビティの型名。|  
|ParentDisplayName|xs:string|親アクティビティの表示名。|  
|ParentInstanceId|xs:string|親アクティビティのインスタンス ID。|  
|CompletedActivity|xs:string|完了したアクティビティの型名。|  
|CompletedActivityDisplayName|xs:string|完了したアクティビティの表示名。|  
|CompletedActivityInstanceId|xs:string|完了したアクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
