---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: d3f27c6ed28efe9d099dcedfc676b839ae9b1dee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275841"
---
# <a name="4202---startsqlcommandexecute"></a>4202 - StartSqlCommandExecute

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|4202|  
|Keywords|WFInstanceStore|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 SQL コマンドが実行されることを示します。  
  
## <a name="message"></a>Message  

 SQL コマンドの実行を開始します: %1  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:string|実行された SQL コマンド。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
