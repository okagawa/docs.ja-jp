---
description: '詳細情報: 3507-ServiceEndpointAdded'
title: 3507 - ServiceEndpointAdded
ms.date: 03/30/2017
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
ms.openlocfilehash: 7de51cb8908d3bf4b450c545c1a4c0f2bdc6a453
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631477"
---
# <a name="3507---serviceendpointadded"></a>3507 - ServiceEndpointAdded

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|3507|  
|Keywords|WFServices|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 サービス エンドポイントが追加されていることを示します。  
  
## <a name="message"></a>Message  

 アドレス '%1'、バインド '%2'、コントラクト '%3' のサービス エンドポイントが追加されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|Address|xs:string|エンドポイントのアドレス。|  
|バインド|xs:string|エンドポイントのバインド。|  
|コントラクト|xs:string|エンドポイントのコントラクト。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
