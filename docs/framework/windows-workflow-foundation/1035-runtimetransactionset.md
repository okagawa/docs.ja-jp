---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: b8bf8431c4e2b82c6aac95820eb45de2a404e976
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294275"
---
# <a name="1035---runtimetransactionset"></a>1035 - RuntimeTransactionSet

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1035|  
|Keywords|WFRuntime|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 アクティビティがランタイムのトランザクションを設定したことを示します。  
  
## <a name="message"></a>Message  

 Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' によってランタイムトランザクションが設定されました。  実行がアクティビティ ' %4 '、DisplayName: ' %5 '、InstanceId: ' %6 ' に分離されています。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|IsolatedActivity|xs:string|トランザクションが分離されるアクティビティの型の名前。|  
|IsolatedActivityDisplayName|xs:string|トランザクションが分離されるアクティビティの表示名。|  
|IsolatedActivityInstanceId|xs:string|トランザクションが分離されるアクティビティのインスタンスの ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
