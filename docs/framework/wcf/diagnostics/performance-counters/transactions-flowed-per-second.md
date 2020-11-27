---
title: 1 秒あたりのトランザクション フロー
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: b47219bd58a9b6c4401baa73177928ddca5b6a8b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254143"
---
# <a name="transactions-flowed-per-second"></a>1 秒あたりのトランザクション フロー

カウンター名 : 1 秒あたりのトランザクション フロー  
  
## <a name="description"></a>Description  

 この操作に対して実行された 1 秒あたりのトランザクションの数です。 このカウンターは、操作に送信されたメッセージにトランザクション ID が存在する場合にインクリメントされます。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
