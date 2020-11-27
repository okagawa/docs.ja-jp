---
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: d74aa77aff7b45b50f6891c999889011d9e03381
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278857"
---
# <a name="218---clientoperationcompleted"></a>218 - ClientOperationCompleted

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|218|  
|Keywords|Troubleshooting、ServiceModel|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、ある操作が完了した直後にクライアントによって生成されます。 一方向の操作の場合は、メッセージが正常に送信された直後に生成されます。 要求 - 応答の操作の場合は、応答の受信後に生成されます。  
  
## <a name="message"></a>Message  

 クライアントは '%2' コントラクトと関連付けられている Action '%1' の実行を完了しました。 メッセージは '%3' に送信されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクション|xs:string|送信メッセージの SOAP アクション ヘッダー。|  
|Contract Name|`xs:string`|コントラクトの名前。 例: ICalculator。|  
|宛先|`xs:string`|メッセージの送信先のサービス エンドポイントのアドレス。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
