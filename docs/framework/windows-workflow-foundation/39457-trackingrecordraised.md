---
title: 39457 - TrackingRecordRaised
ms.date: 03/30/2017
ms.assetid: 5a2731d1-c731-4b79-bb69-016cb69ef481
ms.openlocfilehash: 5bf343f29528bdb3941e253b2fd5b39799d94c2a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275906"
---
# <a name="39457---trackingrecordraised"></a>39457 - TrackingRecordRaised

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|39457|  
|Keywords|WFRuntime|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 TrackingRecord が TrackingParticipant に発生したことを示します。  
  
## <a name="message"></a>Message  

 追跡レコード %1 が %2 になりました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:string|追跡レコード番号。|  
|ParticipantId|xs:string|追跡参加要素|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
