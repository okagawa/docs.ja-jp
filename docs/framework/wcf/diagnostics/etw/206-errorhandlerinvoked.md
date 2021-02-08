---
description: '詳細については、次を参照してください: 206-Errorハンドラが呼び出されました'
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: addbcbdea25c7f8e7515b743e98e426476fa0b28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783782"
---
# <a name="206---errorhandlerinvoked"></a>206 - ErrorHandlerInvoked

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|206|  
|Keywords|Troubleshooting、ServiceModel|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、サービス操作中に発生した例外を処理する機会が `ErrorHandler` に与えられた後に、生成されます。  
  
## <a name="message"></a>Message  

 ディスパッチャーが型 ' %1 ' の ErrorHandler を呼び出しましたが、型 ' %3 ' の例外が発生しました。 ErrorHandled == '%2'。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|呼び出された `ErrorHandler` の型の CLR FullName。|  
|処理済み|`xs:unsignedByte`|エラー ハンドラーがエラーを処理した場合は `true`。それ以外の場合は `false`。|  
|ExceptionTypeName|`xs:string`|処理対象である例外の CLR FullName。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
