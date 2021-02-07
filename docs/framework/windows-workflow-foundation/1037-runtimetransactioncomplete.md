---
description: '詳細情報: 1037-RuntimeTransactionComplete'
title: 1037 - RuntimeTransactionComplete
ms.date: 03/30/2017
ms.assetid: 2c8c31e0-42a9-4f46-865b-2da9ab16a0ba
ms.openlocfilehash: 5784dc1b0eede5ddad0e6aae4cb79c6e859f325e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667864"
---
# <a name="1037---runtimetransactioncomplete"></a>1037 - RuntimeTransactionComplete

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|1037|  
|Keywords|WFRuntime|  
|Level|"詳細"|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 ランタイム トランザクションが完了したことを示します。  
  
## <a name="message"></a>Message  

 ランタイム トランザクションは '%1' の状態で完了しました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|State|xs:string|トランザクションの状態。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
