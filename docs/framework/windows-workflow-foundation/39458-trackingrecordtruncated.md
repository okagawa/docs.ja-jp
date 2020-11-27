---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: f02a34673c51be6e0b127a64e4622131575d836f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275893"
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|39458|  
|Keywords|WFTracking|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 追跡レコードが省略されたことを示します。 変数、注釈、ユーザー データは削除されています。  
  
## <a name="message"></a>Message  

 プロバイダー %2 の ETW セッションに書き込まれた追跡レコード %1 が切り捨てられました。 変数/注釈/ユーザー データは削除されました  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:string|追跡レコード番号。|  
|ProviderId|xs:string|ETW プロバイダー ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
