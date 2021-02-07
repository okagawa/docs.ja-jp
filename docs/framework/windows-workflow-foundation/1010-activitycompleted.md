---
description: 詳細については、「1010-ActivityCompleted」を参照してください。
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: c72339449b94b0ea5d6d8fa227b606cc25c29704
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755539"
---
# <a name="1010---activitycompleted"></a>1010 - ActivityCompleted

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1010|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 アクティビティが実行を完了したことを示します。  
  
## <a name="message"></a>Message  

 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' が状態 '%4' で完了しました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|State|xs:string|アクティビティの状態。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
