---
description: '詳細情報: 1125-InvokeMethodIsNotStatic'
title: 1125 - InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: cd63b7b75121a70f7d7bad6a799827971aa4eae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667370"
---
# <a name="1125---invokemethodisnotstatic"></a>1125 - InvokeMethodIsNotStatic

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1125|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的ではないことを示します。  
  
## <a name="message"></a>Message  

 InvokeMethod '%1' - メソッドは Static ではありません。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|InvokeMethod アクティビティの表示名。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
