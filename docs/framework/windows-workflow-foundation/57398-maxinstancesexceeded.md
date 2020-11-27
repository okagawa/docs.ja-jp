---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: bd490aad24fba4550bc778799cd6f836dcfd466c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289179"
---
# <a name="57398---maxinstancesexceeded"></a>57398 - MaxInstancesExceeded

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|57398|  
|Keywords|WFServices|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 システムがスロットル 'MaxConcurrentInstances' に設定された制限に達したことを示します。  
  
## <a name="message"></a>Message  

 システムはスロットル 'MaxConcurrentInstances' に設定された制限に達しました。 このスロットルの制限は %1 に設定されました。 スロットル値を変更するには、serviceThrottle 要素の属性 'maxConcurrentInstances' を変更するか、動作 ServiceThrottlingBehavior の 'MaxConcurrentInstances' プロパティを変更する必要があります。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|名前|xs:string|項目の名前。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
