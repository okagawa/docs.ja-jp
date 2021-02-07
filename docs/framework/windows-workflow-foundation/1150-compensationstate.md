---
description: '詳細情報: 1150-CompensationState'
title: 1150 - CompensationState
ms.date: 03/30/2017
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
ms.openlocfilehash: 4adc246cbe46dee3594bc6c0330c8e0306489219
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703342"
---
# <a name="1150---compensationstate"></a>1150 - CompensationState

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1150|  
|Keywords|WFActivities|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 CompensableActivity の状態の変更を示します。  
  
## <a name="message"></a>Message  

 CompensableActivity '%1' は '%2' 状態です。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|アクティビティの表示名。|  
|State|xs:string|補正の状態。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
