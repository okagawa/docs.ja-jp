---
description: '詳細情報: 302-Userdefinedwarnings が発生しました'
title: 302 - UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: eb79e32d8993ec60c05e5aaaee1b5e15ee7e32e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794222"
---
# <a name="302---userdefinedwarningoccurred"></a>302 - UserDefinedWarningOccurred

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|302|  
|Keywords|Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、ユーザー コードから生成されます。 開発者は、カスタム定義の警告イベントがサービスで発生したときに、このイベントを生成できます。 これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。 また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。  
  
## <a name="message"></a>Message  

 名前:'%1'、参照:'%2'、ペイロード:%3  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|名前|`xs:string`|イベントのユーザー定義名。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|ペイロード|`xs:string`|イベントのユーザー定義ペイロード。|
