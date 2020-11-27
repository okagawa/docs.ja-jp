---
title: 'エンドポイント : 1 秒あたりの呼び出し回数'
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: 3c9f9882be935474ec187e2829e8e1e58b091afa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253155"
---
# <a name="endpoint-calls-per-second"></a>エンドポイント : 1 秒あたりの呼び出し回数

カウンター名 : 1 秒あたりの呼び出し  
  
## <a name="description"></a>Description  

 このエンドポイントが 1 秒あたりに呼び出される回数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
