---
description: '詳細情報: 301-UserDefinedErrorOccurred'
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 15e12bb27e3626f80747498a1387aa90fc461d28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794248"
---
# <a name="301---userdefinederroroccurred"></a>301 - UserDefinedErrorOccurred

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|301|  
|Keywords|Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring|  
|Level|エラー|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、ユーザー コードから生成されます。 開発者は、カスタム定義のエラー イベントがサービスで発生したときに、このイベントを生成できます。 これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。 また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。  
  
## <a name="message"></a>Message  

 名前:'%1'、参照:'%2'、ペイロード:%3  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|名前|`xs:string`|イベントのユーザー定義名。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|ペイロード|`xs:string`|イベントのユーザー定義ペイロード。|
