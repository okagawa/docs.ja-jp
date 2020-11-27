---
title: 2578 - TryCatchExceptionFromCatchOrFinally
ms.date: 03/30/2017
ms.assetid: 4803fee6-b8d8-4937-9907-d5c5fd5299db
ms.openlocfilehash: 92503b13f59556fa21d058578982c3fa7b7a6b96
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271199"
---
# <a name="2578---trycatchexceptionfromcatchorfinally"></a>2578 - TryCatchExceptionFromCatchOrFinally

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|2578|  
|Keywords|WFActivities|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 Catch または Finally アクティビティから例外がスローされたことを示します。  
  
## <a name="message"></a>Message  

 TryCatch アクティビティ '%1' に関連付けられている Catch または Finally アクティビティは例外をスローしました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|アクティビティの表示名。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
