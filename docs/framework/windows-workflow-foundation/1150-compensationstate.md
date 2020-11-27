---
title: 1150 - CompensationState
ms.date: 03/30/2017
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
ms.openlocfilehash: 2adb317521b8659c2419e4c04aabf4cf4499b36f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285110"
---
# <a name="1150---compensationstate"></a>1150 - CompensationState

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1150|  
|Keywords|WFActivities|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 CompensableActivity の状態の変更を示します。  
  
## <a name="message"></a>Message  

 CompensableActivity '%1' は '%2' 状態です。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|アクティビティの表示名。|  
|State|xs:string|補正の状態。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
