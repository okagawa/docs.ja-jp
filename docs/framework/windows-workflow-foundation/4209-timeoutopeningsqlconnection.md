---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: 9aa8cdffebb0cdf8b1e8225a394edf78ecf032b9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238679"
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 - TimeoutOpeningSqlConnection

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|4209|  
|Keywords|WFInstanceStore|  
|Level|エラー|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 SQL 接続を開こうとしてタイムアウトが発生したことを示します。  
  
## <a name="message"></a>Message  

 SQL 接続を開こうとしてタイムアウトしました。 割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|タイムアウト|xs:string|SQL 接続を開く場合のタイムアウト値。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
