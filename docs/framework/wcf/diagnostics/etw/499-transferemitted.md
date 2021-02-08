---
description: '詳細については、次を参照してください: 499-TransferEmitted'
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: d9802ef718ce6091abe1d1092ad6bb7e7fff108a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783574"
---
# <a name="499---transferemitted"></a>499 - TransferEmitted

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|499|  
|Keywords|Troubleshooting、UserEvents、EndToEndMonitoring、ServiceModel、WFTracking、ServiceHost、WCFMessageLogging|  
|Level|LogAlways|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、転送イベントが発生したときに生成されます。  
  
## <a name="message"></a>Message  

 転送イベントが作成されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
