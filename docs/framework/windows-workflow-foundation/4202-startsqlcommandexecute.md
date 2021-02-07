---
description: '詳細情報: 4202-StartSqlCommandExecute'
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 1282f275933eff0effbda75851e33531c55adb36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755335"
---
# <a name="4202---startsqlcommandexecute"></a>4202 - StartSqlCommandExecute

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|4202|  
|Keywords|WFInstanceStore|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 SQL コマンドが実行されることを示します。  
  
## <a name="message"></a>Message  

 SQL コマンドの実行を開始します: %1  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:string|実行された SQL コマンド。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
