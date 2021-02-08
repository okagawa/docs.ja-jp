---
description: '詳細情報: 222-OperationFailed'
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: ea07dbabb651413f213db6789f2af8059d2595c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794300"
---
# <a name="222---operationfailed"></a>222 - OperationFailed

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|222|  
|Keywords|EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、サービス モデルの既定の `OperationInvoker` が、そのメソッドを呼び出している間に例外に遭遇すると生成されます。 `FaultException` から派生する例外では、このイベントは生成されません。  
  
## <a name="message"></a>Message  

 OperationInvoker によって呼び出されたメソッド '%1' で、ハンドルされない例外がスローされました。 メソッド呼び出し時間は '%2' ミリ秒でした。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|メソッド名|`xs:string`|`OperationInvoker` によって呼び出されたメソッドの CLR 名。|  
|Duration|`xs:long`|`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
