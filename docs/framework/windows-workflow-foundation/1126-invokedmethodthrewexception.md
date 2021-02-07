---
description: '詳細情報: 1126-InvokedMethodThrewException'
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 35c4311a4ab7750cc54a5c9ffb379f34b1cb12aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667357"
---
# <a name="1126---invokedmethodthrewexception"></a>1126 - InvokedMethodThrewException

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1126|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 InvokeMethod アクティビティによって呼び出されたメソッドにより、例外がスローされたことを示します。  
  
## <a name="message"></a>Message  

 アクティビティ '%1' によって呼び出されたメソッドで例外がスローされました。 %2  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|InvokeMethod アクティビティの表示名。|  
|例外|xs:string|例外の詳細|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
