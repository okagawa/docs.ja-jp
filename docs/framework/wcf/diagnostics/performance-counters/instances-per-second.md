---
description: '詳細情報: 1 秒あたりのインスタンス数'
title: 1 秒あたりのインスタンス
ms.date: 03/30/2017
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
ms.openlocfilehash: cfcdd85bef8b1873101c1bbb63ce40bd161a97f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655306"
---
# <a name="instances-per-second"></a>1 秒あたりのインスタンス

カウンター名 : 1 秒あたりに作成されたインスタンス。  
  
## <a name="description"></a>説明  

 1 秒あたりに作成されたサービス インスタンスの合計数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
