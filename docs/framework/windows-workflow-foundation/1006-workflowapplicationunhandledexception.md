---
description: '詳細情報: 1006-WorkflowApplicationUnhandledException'
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: bfccd0d12c5dac4caad1e84e95f1cd096a551aa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755591"
---
# <a name="1006---workflowapplicationunhandledexception"></a>1006 - WorkflowApplicationUnhandledException

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1006|  
|Keywords|WFRuntime|  
|Level|エラー|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 ワークフロー アプリケーションでハンドルされない例外が検出されたことを示します。  
  
## <a name="message"></a>Message  

 WorkflowInstance Id: ' %1 ' でハンドルされない例外が発生しました。  Activity ' %2 '、DisplayName: ' %3 ' から例外が発生しました。  次のアクションが実行されます: %4。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|ワークフローのインスタンス ID|  
|例外|`xs:string`|例外の詳細|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
