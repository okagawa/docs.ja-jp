---
description: '詳細情報: 4201-EndSqlCommandExecute'
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: e0b98e8da5a0a284bfa55e97f5dde25a2ce42b42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755370"
---
# <a name="4201---endsqlcommandexecute"></a>4201 - EndSqlCommandExecute

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|4201|  
|Keywords|WFInstanceStore|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 SQL コマンドの実行が完了したことを示します。  
  
## <a name="message"></a>Message  

 SQL コマンドの実行を終了します: %1  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:string|実行された SQL コマンド。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
