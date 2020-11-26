---
title: 451 - MessageLogInfo
ms.date: 03/30/2017
ms.assetid: 485b4b29-dc21-4a35-93f8-5f4726d6aa5a
ms.openlocfilehash: 2b5dd36099e1d9978cb1136462c224a79465f823
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242787"
---
# <a name="451---messageloginfo"></a>451 - MessageLogInfo

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|451|  
|Keywords|Troubleshooting、WCFMessageLogging|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、メッセージ ログ情報が送信されるときに出力されます。  
  
## <a name="message"></a>Message  

 %1  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|data1|`xs:string`||  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
