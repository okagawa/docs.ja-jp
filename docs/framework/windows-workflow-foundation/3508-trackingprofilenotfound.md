---
description: 詳細については、「3508-TrackingProfileNotFound」を参照してください。
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 3e97af1689a868fb103b06413a0c4f28b0c1f652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778010"
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|3508|  
|Keywords|WFServices|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 構成ファイル内に TrackingProfile がないか、または ActivityDefinitionId がプロファイルと一致していないことを示します。  
  
## <a name="message"></a>Message  

 ActivityDefinitionId '%2' の TrackingProfile '%1' が見つかりません。 config ファイルに TrackingProfile がないか、ActivityDefinitionId が一致しません。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:string|追跡プロファイルの名前。|  
|ActivityDefinitionId|xs:string|アクティビティ定義 ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
