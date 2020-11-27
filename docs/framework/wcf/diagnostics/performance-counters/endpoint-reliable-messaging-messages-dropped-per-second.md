---
title: 'エンドポイント: 信頼できるメッセージの 1 秒あたりの破棄されたメッセージ'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: b8c0f91b2de5d023232756159a50236574308954
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290843"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a>エンドポイント: 信頼できるメッセージの 1 秒あたりの破棄されたメッセージ

カウンター名 : 1 秒あたりに破棄された信頼できるメッセージ セッション  
  
## <a name="description"></a>Description  

 このエンドポイントで 1 秒間に破棄された信頼できるメッセージング メッセージの合計数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
