---
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 1dab44e3fb97d74a2146f5bf992225222bc93d50
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280378"
---
# <a name="4210---sqlexceptioncaught"></a>4210 - SqlExceptionCaught

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|4210|  
|Keywords|WFInstanceStore|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 SQL 例外が発生したことを示します。  
  
## <a name="message"></a>Message  

 SQL 例外番号 %1 メッセージ %2 がキャッチされました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs:string|SQL エラー番号。|  
|ExceptionMessage|xs:string|SQL 例外からのメッセージ。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
