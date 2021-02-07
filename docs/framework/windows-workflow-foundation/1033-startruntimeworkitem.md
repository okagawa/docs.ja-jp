---
description: '詳細情報: 1033-StartRuntimeWorkItem'
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: 31e664070b7592d3350a2f6f84f0493cc8f11ea1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668007"
---
# <a name="1033---startruntimeworkitem"></a>1033 - StartRuntimeWorkItem

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1033|  
|Keywords|WFRuntime|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 RuntimeWorkItem が実行を開始していることを示します。  
  
## <a name="message"></a>Message  

 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目の実行を開始しています。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
