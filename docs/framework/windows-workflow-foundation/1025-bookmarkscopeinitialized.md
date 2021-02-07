---
description: '詳細情報: 1025-BookmarkScopeInitialized'
title: 1025 - BookmarkScopeInitialized
ms.date: 03/30/2017
ms.assetid: 63584434-e709-471d-9e96-97d3d99e70d6
ms.openlocfilehash: 22e686253fc5d580fba453950825072667247fad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755500"
---
# <a name="1025---bookmarkscopeinitialized"></a>1025 - BookmarkScopeInitialized

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1025|  
|Keywords|WFRuntime|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 BookmarkScope が初期化されていることを示します。  
  
## <a name="message"></a>Message  

 TemporaryId: '%1' を指定されていた BookmarkScope が ID: '%2' で初期化されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|TemporaryId|xs:string|ブックマークの一時 ID。|  
|InitializedId|xs:string|ブックマークの初期化された ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
