---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 9249bdd0fe996ee7c1b04783ac8fef2c48063cc0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294158"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a>1132 - InvokeMethodDoesNotUseAsyncPattern

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1132|  
|Keywords|WFRuntime|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 CacheMetadata 手順内で、InvokeMethod アクティビティがメソッドを呼び出すときに非同期パターンを使用しないことを示します。  
  
## <a name="message"></a>Message  

 InvokeMethod '%1' - メソッドでは非同期パターンを使用しません。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|InvokeMethod アクティビティの表示名。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
