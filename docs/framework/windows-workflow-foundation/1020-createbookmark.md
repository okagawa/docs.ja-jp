---
description: '詳細情報: 1020-CreateBookmark'
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 39796eaf68d9cb52e9faa2605fc21955a2c167ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792844"
---
# <a name="1020---createbookmark"></a>1020 - CreateBookmark

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1020|  
|Keywords|WFRuntime|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 あるアクティビティ用のブックマークが作成されたことを示します。  
  
## <a name="message"></a>Message  

 Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' のブックマークが作成されました。  BookmarkName: %4、BookmarkScope: %5。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|BookmarkName|xs:string|ブックマークの名前。|  
|BookmarkScope|xs:string|ブックマークのスコープ。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
