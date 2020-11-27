---
title: 210 - MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: a0da1c198700407d8cdf699d1b734247024717a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267742"
---
# <a name="210---messagethrottleexceeded"></a>210 - MessageThrottleExceeded

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|210|  
|Keywords|EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、3 つの主要なサービス スロットルの 1 つを超過したときに生成されます。 このイベントが生成されるのは、最初にスロットル制限を超過したときのみです。 たとえば、同時呼び出しのスロットル制限が 10 の場合は、11 番目の同時呼び出しが `MessageThrottleExceeded` イベントになります。 12 番目の呼び出しが別のイベントになることはありません。 また、イベント ストリームが煩雑になるのを避けるため、制限値の前後のアクティビティの結果が別のイベントになることはありません。 この例では、2 つの呼び出しが完了した場合、9 つの同時呼び出しが行われます。 続いて 2 つの呼び出しが行われた場合は、現在の値が再び 11 になります。 これは、別のイベントにはなりません。 現在の値がスロットル制限の 70% になると、アクティビティの遅れを示す別のイベントが生成されます。 以降のアクティビティが制限を超えた場合は、別の `MessageThrottleExceeded` イベントが生成されます。 この例では、同時呼び出しの数が 7 になり、再び 11 に達すると、別の `MessageThrottleExceeded` イベントが生成されます。  
  
## <a name="message"></a>Message  

 スロットル '%1' の '%2' の制限に達しました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|Throttle Name|`xs:string`|超過したスロットルの名前。 `MaxConcurrentCalls`、`MaxConcurrentInstances`、または `MaxConcurrentSessions`。|  
|制限|`xs:long`|現在構成されている、スロットルの制限。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
