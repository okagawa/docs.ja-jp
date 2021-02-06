---
description: '詳細情報: 3552-MaxPendingMessagesPerChannelExceeded'
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: 5fb2d27f7d68716cebf2cfaafd21851226a456e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631438"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 - MaxPendingMessagesPerChannelExceeded

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|3552|  
|Keywords|クォータ、WFServices|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 スロットル 'MaxPendingMessagesPerChannel' の制限に達したことを示します。  
  
## <a name="message"></a>Message  

 '%1' のスロットル 'MaxPendingMessagesPerChannel' の制限に達しました。 この制限を引き上げるには、BufferedReceiveServiceBehavior の MaxPendingMessagesPerChannel プロパティを調整してください。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|制限|xs:string|MaxPendingMessagesPerChannel スロットルの制限。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
