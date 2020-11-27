---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: 088754cb15c2e55faa1d43a1da1c79ddcddd69f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280417"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a>4208 - RetryingSqlCommandDueToSqlError

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|4208|  
|Keywords|WFInstanceStore|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 SQL プロバイダーは SQL エラーのために SQL コマンドを再試行していることを示します。  
  
## <a name="message"></a>Message  

 SQL エラー番号 %1 のため、SQL コマンドを再試行します。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs:string|SQL エラー番号。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
