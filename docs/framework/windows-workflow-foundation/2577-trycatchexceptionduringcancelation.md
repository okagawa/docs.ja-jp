---
description: '詳細情報: 2577-TryCatchExceptionDuringCancelation'
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: e02e7722dadfe38b9fc1fbb92e809ae8f80cbd2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778101"
---
# <a name="2577---trycatchexceptionduringcancelation"></a>2577 - TryCatchExceptionDuringCancelation

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|2577|  
|Keywords|WFActivities|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 TryCatch アクティビティの子アクティビティが取り消し中に例外をスローしたことを示します。  
  
## <a name="message"></a>Message  

 TryCatch アクティビティ '%1' の子アクティビティは取り消し中に例外をスローしました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|アクティビティの表示名。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
