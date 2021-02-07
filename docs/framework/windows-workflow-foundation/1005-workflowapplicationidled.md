---
description: 詳細については、「1005-WorkflowApplicationIdled」を参照してください。
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: ee8d0b7ff2155333213a718a04c3966024fda89d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755604"
---
# <a name="1005---workflowapplicationidled"></a>1005 - WorkflowApplicationIdled

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1005|  
|Keywords|WFRuntime|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 ワークフロー アプリケーションがアイドル状態になったことを示します。  
  
## <a name="message"></a>Message  

 WorkflowApplication ID: '%1' がアイドル状態になりました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|ワークフロー アプリケーション ID|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
