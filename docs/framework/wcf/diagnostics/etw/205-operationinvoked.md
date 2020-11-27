---
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: c36294a4a430c3e372e8213246e85dba45ce03c8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286020"
---
# <a name="205---operationinvoked"></a>205 - OperationInvoked

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|205|  
|Keywords|Troubleshooting、ServiceModel|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、サービス モデルの既定の `OperationInvoker` がメソッドの呼び出しを開始する直前に生成されます。  
  
## <a name="message"></a>Message  

 OperationInvoker が '%1' メソッドを呼び出しました。 呼び出し元の情報: '%2'。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|メソッド名|`xs:string`|`OperationInvoker` によって呼び出されたメソッドの CLR 名。|  
|呼び出し元情報|`xs:string`|クライアントの IP アドレスとポート番号。'&lt;IP アドレス&gt;:&lt;ポート番号&gt;' の形式で指定します。 この 2 つの値は、操作コンテキスト内の 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' メッセージ プロパティから取得します。 TCP 以外のバインドの場合、この値は `null` になることに注意してください。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
