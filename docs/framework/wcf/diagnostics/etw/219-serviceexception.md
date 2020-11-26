---
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: 832ced406b6079fad8f4b9bea512a6d390bdcc0f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241942"
---
# <a name="219---serviceexception"></a>219 - ServiceException

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|219|  
|Keywords|EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel|  
|Level|エラー|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、WCF サービスがハンドルされない例外を検出した場合に生成されます。 これには、アクティベーション中のハンドルされない例外、メッセージ処理中のハンドルされない例外、およびユーザー コード内でのハンドルされない例外が含まれます。  
  
## <a name="message"></a>Message  

 メッセージの処理中に種類 '%2' のハンドルされない例外がスローされました。 完全な例外 ToString: %1。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|CLR 例外に対して `ToString`() を呼び出した結果。|  
|ExceptionTypeName|`xs:string`|例外の型の CLR FullName。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
