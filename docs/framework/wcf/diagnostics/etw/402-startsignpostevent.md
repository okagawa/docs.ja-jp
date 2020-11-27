---
title: 402 - StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
ms.openlocfilehash: ff32c900f4e357b7f1eca669a0ea60f80ea24b19
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258323"
---
# <a name="402---startsignpostevent"></a>402 - StartSignpostEvent

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|402|  
|Keywords|トラブルシューティング|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、エンド ツー エンド アクティビティの開始を示します。 ここにはアクティビティの名前が指定されています。  
  
## <a name="message"></a>Message  

 アクティビティの境界  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|Extended Data|`xs:string`|アクティビティの名前。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
