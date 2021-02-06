---
description: '詳細情報: 1 秒あたりに破棄された信頼できるメッセージメッセージ'
title: 信頼できるメッセージの 1 秒あたりの破棄されたメッセージ
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 6132316f100cecdba357a6da071e23de8c9a2181
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655111"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>信頼できるメッセージの 1 秒あたりの破棄されたメッセージ

カウンター名 : 1 秒あたりに破棄された信頼できるメッセージ セッション  
  
## <a name="description"></a>説明  

 このサービスで 1 秒間に破棄された信頼できるメッセージング メッセージの合計数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
