---
title: 1146 - FlowchartSwitchCase
ms.date: 03/30/2017
ms.assetid: 274e9209-1720-4512-a615-e742f00895f4
ms.openlocfilehash: 9636e5371440229ced965cf125ffb2ce4e314f72
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286111"
---
# <a name="1146---flowchartswitchcase"></a>1146 - FlowchartSwitchCase

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1146|  
|Keywords|WFActivities|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 フローチャート スイッチで、どの例が選択されたかを示します。  
  
## <a name="message"></a>Message  

 フローチャート '%1'/FlowSwitch - Case '%2' が選択されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|FlowChart|xs:string|FlowChart の表示名。|  
|ケース|xs:string|選択したスイッチに示します。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
