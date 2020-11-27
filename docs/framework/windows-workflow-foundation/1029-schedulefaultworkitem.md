---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: 5c109607b2d353d3d4a5a693f29ab66bb76c8398
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275090"
---
# <a name="1029---schedulefaultworkitem"></a>1029 - ScheduleFaultWorkItem

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1029|  
|Keywords|WFRuntime|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 FaultWorkItem がスケジュールされていることを示します。  
  
## <a name="message"></a>Message  

 Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' に対して FaultWorkItem がスケジュールされました。  Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|エラーとなったアクティビティの型名。|  
|FaultActivityDisplayName|xs:string|エラーとなったアクティビティの表示名。|  
|FaultActivityInstanceId|xs:string|エラーとなったアクティビティのインスタンス ID。|  
|ExceptionActivity|xs:string|例外をスローしたアクティビティの型名。|  
|ExceptionActivityDisplayName|xs:string|例外をスローしたアクティビティの表示名。|  
|ExceptionActivityInstanceId|xs:string|例外をスローしたアクティビティのインスタンス ID。|  
|例外|xs:string|例外の詳細|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
