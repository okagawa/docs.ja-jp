---
description: 詳細については、「4210-SqlExceptionCaught」を参照してください。
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 58846d02b6d1e388e3aef2bff76f51cba4990f2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777880"
---
# <a name="4210---sqlexceptioncaught"></a>4210 - SqlExceptionCaught

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|4210|  
|Keywords|WFInstanceStore|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 SQL 例外が発生したことを示します。  
  
## <a name="message"></a>Message  

 SQL 例外番号 %1 メッセージ %2 がキャッチされました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs:string|SQL エラー番号。|  
|ExceptionMessage|xs:string|SQL 例外からのメッセージ。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
