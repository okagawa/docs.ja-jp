---
description: '詳細情報: 207-FaultProviderInvoked 呼び出されました'
title: 207 - FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 03c4f1669fc61019ccf4d23d2994f136e231fbec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728068"
---
# <a name="207---faultproviderinvoked"></a>207 - FaultProviderInvoked

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|207|  
|Keywords|Troubleshooting、ServiceModel|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、`FaultProvider` が呼び出された後に生成されます。  
  
## <a name="message"></a>Message  

 ディスパッチャーが型 '%1' の FaultProvider を呼び出し、種類 '%2' の例外がスローされました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|呼び出された `FaultProvider` の型の CLR FullName。|  
|ExceptionTypeName|`xs:string`|`FaultProvider` の操作対象である例外の CLR FullName。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
