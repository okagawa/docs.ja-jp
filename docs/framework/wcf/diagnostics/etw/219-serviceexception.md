---
description: '詳細情報: 219-ServiceException'
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: b2ac12d6c5c68517b085b39dd7d0f81c39db9ebd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794326"
---
# <a name="219---serviceexception"></a>219 - ServiceException

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|219|  
|Keywords|EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel|  
|Level|エラー|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、WCF サービスがハンドルされない例外を検出した場合に生成されます。 これには、アクティベーション中のハンドルされない例外、メッセージ処理中のハンドルされない例外、およびユーザー コード内でのハンドルされない例外が含まれます。  
  
## <a name="message"></a>Message  

 メッセージの処理中に種類 '%2' のハンドルされない例外がスローされました。 完全な例外 ToString: %1。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|CLR 例外に対して `ToString`() を呼び出した結果。|  
|ExceptionTypeName|`xs:string`|例外の型の CLR FullName。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
