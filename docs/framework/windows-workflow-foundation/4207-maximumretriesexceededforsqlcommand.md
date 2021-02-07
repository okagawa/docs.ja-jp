---
description: '詳細情報: 4207-MaximumRetriesExceededForSqlCommand'
title: 4207 - MaximumRetriesExceededForSqlCommand
ms.date: 03/30/2017
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
ms.openlocfilehash: e831da08e37010afaa33f3a52cd7cf7a9b4d713b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742720"
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a>4207 - MaximumRetriesExceededForSqlCommand

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|4207|  
|Keywords|クオータ、WFInstanceStore|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 再試行が最大実行回数実行されたので、SQL プロバイダーは SQL コマンドの再試行を停止しようとしていることを示します。  
  
## <a name="message"></a>Message  

 SQL コマンドが最大実行回数実行されたので、この SQL コマンドの再試行を停止します。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
