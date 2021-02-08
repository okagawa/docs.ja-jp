---
description: '詳細情報: 214-OperationCompleted'
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: aad1ac49667a2ebbf172b5132507584e05d0f03e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794391"
---
# <a name="214---operationcompleted"></a>214 - OperationCompleted

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|214|  
|Keywords|HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、サービス モデルの既定の `OperationInvoker` が、メソッドから例外がスローされることなく、メソッドへの呼び出しを完了したときに生成されます。  
  
## <a name="message"></a>Message  

 OperationInvoker がメソッド '%1' への呼び出しを完了しました。 メソッド呼び出し時間は '%2' ミリ秒でした。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|メソッド名|`xs:string`|`OperationInvoker` によって呼び出されたメソッドの CLR 名。|  
|Duration|`xs:long`|`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
