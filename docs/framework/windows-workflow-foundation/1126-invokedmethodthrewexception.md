---
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 7caaebe42f49a62fec61ba17a4d3fe3a538e2ab4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262841"
---
# <a name="1126---invokedmethodthrewexception"></a>1126 - InvokedMethodThrewException

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1126|  
|Keywords|WFRuntime|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 InvokeMethod アクティビティによって呼び出されたメソッドにより、例外がスローされたことを示します。  
  
## <a name="message"></a>Message  

 アクティビティ '%1' によって呼び出されたメソッドで例外がスローされました。 %2  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|InvokeMethod アクティビティの表示名。|  
|例外|xs:string|例外の詳細|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
