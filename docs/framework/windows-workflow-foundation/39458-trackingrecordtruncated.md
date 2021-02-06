---
description: '詳細情報: 39458-TrackingRecordTruncated'
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: bb9a46dc5bd9bc4f4709a740dd0e7ec47ca826e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631282"
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|39458|  
|Keywords|WFTracking|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 追跡レコードが省略されたことを示します。 変数、注釈、ユーザー データは削除されています。  
  
## <a name="message"></a>Message  

 プロバイダー %2 の ETW セッションに書き込まれた追跡レコード %1 が切り捨てられました。 変数/注釈/ユーザー データは削除されました  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:string|追跡レコード番号。|  
|ProviderId|xs:string|ETW プロバイダー ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
