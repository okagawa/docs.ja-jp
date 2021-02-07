---
description: '詳細情報: 1011-ScheduleExecuteActivityWorkItem'
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 81010390de2ad01ec3063f2ac89608b97dcb713e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703355"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a>1011 - ScheduleExecuteActivityWorkItem

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1011|  
|Keywords|WFRuntime|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 ExecuteActivityWorkItem がスケジュールされたことを示します。  
  
## <a name="message"></a>Message  

 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して ExecuteActivityWorkItem がスケジュールされました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
