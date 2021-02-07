---
description: '詳細情報: 1146-FlowchartSwitchCase'
title: 1146 - FlowchartSwitchCase
ms.date: 03/30/2017
ms.assetid: 274e9209-1720-4512-a615-e742f00895f4
ms.openlocfilehash: f6e9b33f9c068b51695d3ac46cda51fb6d9f8b3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667071"
---
# <a name="1146---flowchartswitchcase"></a>1146 - FlowchartSwitchCase

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1146|  
|Keywords|WFActivities|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 フローチャート スイッチで、どの例が選択されたかを示します。  
  
## <a name="message"></a>Message  

 フローチャート '%1'/FlowSwitch - Case '%2' が選択されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|FlowChart|xs:string|FlowChart の表示名。|  
|ケース|xs:string|選択したスイッチに示します。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
