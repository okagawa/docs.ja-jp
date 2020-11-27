---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 5e6a5f9d21435fee8309bd222443407e50ec2cee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263608"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 - BufferOutOfOrderMessageNoBookmark

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|3551|  
|Keywords|WFServices|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 ブックマークの再開が失敗したことを示します。 サービス インスタンスがこの特定の操作を処理する準備が整ったら、バッファーされた受信操作が再試行されます。  
  
## <a name="message"></a>Message  

 サービス インスタンス '%1' での操作 '%2' は現時点では実行できません。 サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|操作の名前。|  
|ServiceInstanceId|xs:string|サービス インスタンスの ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
