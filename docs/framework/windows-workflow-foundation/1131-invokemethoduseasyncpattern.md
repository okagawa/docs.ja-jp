---
description: '詳細情報: 1131-InvokeMethodUseAsyncPattern'
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 59d8e5e1fe7c5b038df6fce3211fd01977abc4f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667318"
---
# <a name="1131---invokemethoduseasyncpattern"></a>1131 - InvokeMethodUseAsyncPattern

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1131|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 CacheMetadata の手順では、InvokeMethod アクティビティはメソッドを呼び出すときの非同期パターンを使用していることを示します。  
  
## <a name="message"></a>Message  

 InvokeMethod '%1' - メソッドでは '%2' および '%3' の非同期パターンを使用します。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|InvokeMethod アクティビティの表示名。|  
|BeginMethod|xs:string|begin メソッドの名前。|  
|EndMethod|xs:string|end メソッドの名前。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
