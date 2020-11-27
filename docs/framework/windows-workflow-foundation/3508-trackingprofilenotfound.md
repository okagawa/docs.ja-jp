---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 23262427c3da730eaf930a8b483c7c4d4ec3a3a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289842"
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|3508|  
|Keywords|WFServices|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 構成ファイル内に TrackingProfile がないか、または ActivityDefinitionId がプロファイルと一致していないことを示します。  
  
## <a name="message"></a>Message  

 ActivityDefinitionId '%2' の TrackingProfile '%1' が見つかりません。 config ファイルに TrackingProfile がないか、ActivityDefinitionId が一致しません。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:string|追跡プロファイルの名前。|  
|ActivityDefinitionId|xs:string|アクティビティ定義 ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
