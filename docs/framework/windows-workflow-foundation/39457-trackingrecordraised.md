---
description: '詳細情報: 39457-TrackingRecordRaised'
title: 39457 - TrackingRecordRaised
ms.date: 03/30/2017
ms.assetid: 5a2731d1-c731-4b79-bb69-016cb69ef481
ms.openlocfilehash: 551e13e32dbb690458877ceed0b532799f238966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777906"
---
# <a name="39457---trackingrecordraised"></a>39457 - TrackingRecordRaised

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|39457|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 TrackingRecord が TrackingParticipant に発生したことを示します。  
  
## <a name="message"></a>Message  

 追跡レコード %1 が %2 になりました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:string|追跡レコード番号。|  
|ParticipantId|xs:string|追跡参加要素|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
