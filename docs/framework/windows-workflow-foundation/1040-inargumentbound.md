---
description: '詳細情報: 1040-InArgumentBound'
title: 1040 - InArgumentBound
ms.date: 03/30/2017
ms.assetid: 7dfaad1b-36c0-4575-84c1-31d63b0eaf5d
ms.openlocfilehash: f604a2503bcaf407a9a690b5a681208815fd245a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667799"
---
# <a name="1040---inargumentbound"></a>1040 - InArgumentBound

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1040|  
|Keywords|WFActivities|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 In 引数がバインドされたことを示します。  
  
## <a name="message"></a>Message  

 Activity '%2' の引数 '%1' で、DisplayName: '%3'、InstanceId: '%4' が値: %5 にバインドされています。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InArgument|xs:string|InArgument の名前。|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|値|xs:string|InArgument にバインドされた値。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
