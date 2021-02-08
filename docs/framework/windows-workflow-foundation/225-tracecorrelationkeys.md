---
description: '詳細情報: 225-TraceCorrelationKeys'
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: c5fdb9305815cdc4df6bbae3e54209d2b5cffd9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778114"
---
# <a name="225---tracecorrelationkeys"></a>225 - TraceCorrelationKeys

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|225|  
|Keywords|Troubleshooting、ServiceModel|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、ワークフロー サービスでコンテンツ ベースの相関関係が使用されるときに生成されます。 これには、メッセージとインスタンスの相関関係を定義するために適用されている相関関係キーが含まれます。  
  
## <a name="message"></a>Message  

 親スコープ '%3' の値 '%2' を使用して相関関係キー '%1' が計算されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|Instance Key|`xs:GUID`|相関関係値から生成されたキー。|  
|値|`xs:string`|相関関係インスタンス キーの計算に使用された値。|  
|Parent Scope|`xs:string`||  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。 例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
