---
description: '詳細情報: 401-StopSignPostEvent'
title: 401- StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: 99b6151d902f3f8059b0aa01e6cda290debafda6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793949"
---
# <a name="401--stopsignpostevent"></a>401- StopSignPostEvent

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|401|  
|Keywords|トラブルシューティング|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、エンド ツー エンド アクティビティの終了を示します。 ここにはアクティビティの名前が指定されています。  
  
## <a name="message"></a>Message  

 アクティビティの境界  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|Extended Data|`xs:string`|アクティビティの名前。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
