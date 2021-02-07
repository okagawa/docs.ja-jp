---
description: '詳細については、次を参照してください: 1009-ActivityScheduled'
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 80ee250955a03927fb9db2b1242d420be77a6df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755552"
---
# <a name="1009---activityscheduled"></a>1009 - ActivityScheduled

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1009|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 アクティビティの実行がスケジュールされていることを示します。  
  
## <a name="message"></a>Message  

 Parent Activity '%1'、DisplayName: '%2'、InstanceId: '%3' scheduled child Activity '%4'、DisplayName: '%5'、InstanceId: '%6'。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|親アクティビティの型名。|  
|ParentDisplayName|xs:string|親アクティビティの表示名。|  
|ParentInstanceId|xs:string|親アクティビティのインスタンス ID。|  
|ChildActivity|xs:string|スケジュール済みの子アクティビティの型名。|  
|ChildDisplayName|xs:string|スケジュール済みの子アクティビティの表示名。|  
|ChildInstanceId|xs:string|スケジュール済み子アクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
