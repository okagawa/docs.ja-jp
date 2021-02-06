---
description: 詳細については、「39456-TrackingRecordDropped」を参照してください。
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: 0f6920ef85327318f4ea8662ae36f26c7494bcb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631295"
---
# <a name="39456---trackingrecorddropped"></a>39456 - TrackingRecordDropped

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|39456|  
|Keywords|WFTracking|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 サイズが ETW セッション プロバイダーによって許可される最大値を超えているため、追跡レコードが削除されたことを示します。  
  
## <a name="message"></a>Message  

 追跡レコード %1 のサイズが、プロバイダー %2 の ETW セッションで許可される最大サイズを超えています  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|例外|xs:string|例外の詳細|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
