---
description: 詳細については、「4212-LockRetryTimeout」を参照してください。
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: a2299d0d9643fb60ff420519fb43199e3f747c69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667084"
---
# <a name="4212---lockretrytimeout"></a>4212 - LockRetryTimeout

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|4212|  
|Keywords|WFInstanceStore|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  

 SQL プロバイダーはインスタンス ロックを取得しようとしてタイムアウトを検出しました。  
  
## <a name="message"></a>Message  

 インスタンスのロックを取得しようとしてタイムアウトしました。  割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|遅延|xs:string|再試行間の遅延。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
