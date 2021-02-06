---
description: '詳細情報: 403-SuspendSignpostEvent'
title: 403 - SuspendSignpostEvent
ms.date: 03/30/2017
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
ms.openlocfilehash: 4e601920c94ed99c25a1c969508798f65f5348bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99656424"
---
# <a name="403---suspendsignpostevent"></a>403 - SuspendSignpostEvent

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|403|  
|Keywords|トラブルシューティング|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、エンド ツー エンド アクティビティの中断を示します。 ここにはアクティビティの名前が指定されています。  
  
## <a name="message"></a>Message  

 アクティビティの境界  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|Extended Data|`xs:string`|アクティビティの名前。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
