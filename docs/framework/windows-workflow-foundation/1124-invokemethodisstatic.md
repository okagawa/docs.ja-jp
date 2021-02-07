---
description: '詳細情報: 1124-InvokeMethodIsStatic'
title: 1124 - InvokeMethodIsStatic
ms.date: 03/30/2017
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
ms.openlocfilehash: 86febd9c94c2e4c533eb5ab4349855f6d048a5ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667383"
---
# <a name="1124---invokemethodisstatic"></a>1124 - InvokeMethodIsStatic

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1124|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的であることを示します。  
  
## <a name="message"></a>Message  

 InvokeMethod '%1' - メソッドは Static です。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|InvokeMethod アクティビティの表示名。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
