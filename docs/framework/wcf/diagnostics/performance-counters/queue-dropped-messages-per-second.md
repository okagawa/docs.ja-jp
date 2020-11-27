---
title: 1 秒あたりの破棄されたメッセージのキュー
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 81ba15965676ba7ffe5ca2aaac5e1d0e94e27962
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266039"
---
# <a name="queue-dropped-messages-per-second"></a>1 秒あたりの破棄されたメッセージのキュー

カウンター名: 1 秒あたりの破棄されたメッセージのキュー。  
  
## <a name="description"></a>Description  

 このサービスでキューに置かれたトランスポートによって 1 秒あたりに破棄されたメッセージの数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
