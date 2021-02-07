---
description: '詳細情報: 1002-WorkflowApplicationTerminated'
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 8ceef41515231833767fc7e2095ab3850bf80e41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755629"
---
# <a name="1002---workflowapplicationterminated"></a>1002 - WorkflowApplicationTerminated

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1002|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 例外が発生し、ワークフロー アプリケーションが Faulted 状態で終了したことを示します。  
  
## <a name="message"></a>Message  

 WorkflowApplication ID: %1 は中止されました。 例外により Faulted 状態で完了しました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|`xs:string`|ワークフロー アプリケーション ID|  
|例外|`xs:string`|例外の詳細|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
