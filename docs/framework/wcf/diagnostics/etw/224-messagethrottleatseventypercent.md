---
description: '詳細情報: 224-MessageThrottleAtSeventyPercent'
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: 14c08371c5db7e6f7deb0a5851a1d24dfc94475e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794274"
---
# <a name="224---messagethrottleatseventypercent"></a>224 - MessageThrottleAtSeventyPercent

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|224|  
|Keywords|EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 `MessageThrottleExceeded` イベントは、主要なサービス スロットルの 1 つを超過したときに生成されます。 アクティビティの急増が緩やかになり、スロットルの現在の値が現在の制限の 70% である場合は、このイベントが生成されます。 このイベントは、アクティビティが緩やかになったときに一度だけ生成されます。 現在の値が 70% の基準付近を上下している (70、69、70、71、70、69 など) 場合は、最初に 70% に達したときにイベントが生成されます。 このイベントが生成された後にスロットル制限を超えた場合は、`MessageThrottleExceeded` イベントが生成されます。  
  
## <a name="message"></a>Message  

 スロットル '%1' の '%2' の制限は 70%% です。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|Throttle Name|`xs:string`|超過したスロットルの名前。 `MaxConcurrentCalls`、`MaxConcurrentInstances`、または `MaxConcurrentSessions`。|  
|制限|`xs:long`|現在構成されている、スロットルの制限。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
