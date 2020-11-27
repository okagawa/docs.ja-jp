---
title: 1 秒あたりのキューに置かれた拒否メッセージ
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 2b7686ee94ab051bc255bdb71681c8d1c473094c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276205"
---
# <a name="queued-rejected-messages-per-second"></a>1 秒あたりのキューに置かれた拒否メッセージ

カウンター名 : 1 秒あたりに拒否されたキューに置かれたメッセージ。  
  
## <a name="description"></a>Description  

 このサービスでキューに置かれたトランスポートによって 1 秒あたりに拒否されたメッセージの数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
