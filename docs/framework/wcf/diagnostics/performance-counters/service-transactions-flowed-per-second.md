---
description: '詳細については、「サービス: 1 秒あたりのトランザクションフロー」を参照してください。'
title: 'サービス : 1 秒あたりのトランザクション フロー'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: aae78853272b46a97ce25a710039661f36bf7079
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759498"
---
# <a name="service-transactions-flowed-per-second"></a>サービス : 1 秒あたりのトランザクション フロー

カウンター名 : 1 秒あたりのトランザクション フロー。  
  
## <a name="description"></a>説明  

 このサービスでの操作に対して実行された 1 秒あたりのトランザクションの数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
