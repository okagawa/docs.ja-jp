---
description: '詳細情報: 217-ClientOperationPrepared'
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: eab6a9a654e6e48a8831f238cdf3a3bf7a9f62d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794352"
---
# <a name="217---clientoperationprepared"></a>217 - ClientOperationPrepared

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|217|  
|Keywords|Troubleshooting、ServiceModel|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、操作がサービスに送信される直前に、クライアントによって生成されます。  
  
## <a name="message"></a>Message  

 クライアントは '%2' コントラクトと関連付けられている Action '%1' を実行しています。 メッセージは '%3' に送信されます。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクション|`xs:string`|送信メッセージの SOAP アクション ヘッダー。|  
|Contract Name|`xs:string`|コントラクトの名前。 例: ICalculator。|  
|宛先|`xs:string`|メッセージの送信先となるサービス エンドポイントのアドレス。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
