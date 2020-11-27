---
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 8c9c20fd4fb74f80779c1d2ef8f29ac3d44050d9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275376"
---
# <a name="1020---createbookmark"></a>1020 - CreateBookmark

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1020|  
|Keywords|WFRuntime|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 あるアクティビティ用のブックマークが作成されたことを示します。  
  
## <a name="message"></a>Message  

 Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' のブックマークが作成されました。  BookmarkName: %4、BookmarkScope: %5。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|BookmarkName|xs:string|ブックマークの名前。|  
|BookmarkScope|xs:string|ブックマークのスコープ。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
