---
title: 403 - SuspendSignpostEvent
ms.date: 03/30/2017
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
ms.openlocfilehash: 66251141cdf66c18ad0c1334f6f3e6c0629b4b33
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241058"
---
# <a name="403---suspendsignpostevent"></a>403 - SuspendSignpostEvent

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|403|  
|Keywords|トラブルシューティング|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、エンド ツー エンド アクティビティの中断を示します。 ここにはアクティビティの名前が指定されています。  
  
## <a name="message"></a>Message  

 アクティビティの境界  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|Extended Data|`xs:string`|アクティビティの名前。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
