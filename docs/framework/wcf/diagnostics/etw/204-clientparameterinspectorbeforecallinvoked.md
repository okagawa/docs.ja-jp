---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: a7db8c9fa87518c59969f3089ff033fa8c912577
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275789"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a>204 - ClientParameterInspectorBeforeCallInvoked

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|204|  
|Keywords|Troubleshooting、ServiceModel|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、クライアント パラメーター インスペクターで Service Model が `BeforeCall` メソッドを呼び出した後に生成されます。  
  
## <a name="message"></a>Message  

 ディスパッチャーが型 '%1' の ClientParameterInspector で 'BeforeCall' を呼び出しました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|呼び出されたインスペクターの型の CLR FullName。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
