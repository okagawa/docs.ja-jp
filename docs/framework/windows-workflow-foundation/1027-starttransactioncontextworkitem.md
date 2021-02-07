---
description: '詳細について: 1027-StartTransactionContextWorkItem'
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: e7f81a5998d948d3042b51dcdf20fbb1c88ad266
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755474"
---
# <a name="1027---starttransactioncontextworkitem"></a>1027 - StartTransactionContextWorkItem

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1027|  
|Keywords|WFRuntime|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 TransactionContextWorkItem が実行を開始していることを示します。  
  
## <a name="message"></a>Message  

 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の TransactionContextWorkItem の実行を開始しています。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
