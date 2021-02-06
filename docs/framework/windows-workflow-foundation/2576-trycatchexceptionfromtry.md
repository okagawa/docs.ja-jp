---
description: '詳細情報: 2576-TryCatchExceptionFromTry'
title: 2576 - TryCatchExceptionFromTry
ms.date: 03/30/2017
ms.assetid: 47e48973-b17c-4a16-8338-c84b54aa0a6e
ms.openlocfilehash: 83e26726377a9f8bbedda2a310dcf4ee6928d3a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631526"
---
# <a name="2576---trycatchexceptionfromtry"></a>2576 - TryCatchExceptionFromTry

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|2576|  
|Keywords|WFActivities|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 TryCatch アクティビティが例外をキャッチしたことを示します。  
  
## <a name="message"></a>Message  

 TryCatch アクティビティ '%1' は、型 '%2' の例外をキャッチしました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|アクティビティの表示名。|  
|例外|xs:string|例外の型名。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
