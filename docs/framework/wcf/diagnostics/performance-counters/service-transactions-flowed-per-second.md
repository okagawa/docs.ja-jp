---
title: 'サービス : 1 秒あたりのトランザクション フロー'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: 158bd7e2f2f98e91215ef7351cf90493a2d3059d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236833"
---
# <a name="service-transactions-flowed-per-second"></a>サービス : 1 秒あたりのトランザクション フロー

カウンター名 : 1 秒あたりのトランザクション フロー。  
  
## <a name="description"></a>Description  

 このサービスでの操作に対して実行された 1 秒あたりのトランザクションの数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
