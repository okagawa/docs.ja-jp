---
description: '詳細情報: 1 秒あたりのコミットされたトランザクション操作'
title: 1 秒あたりのコミットされたトランザクション操作
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 019906cccc527a032d91eb20328eddbb6d9aada8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655085"
---
# <a name="transacted-operations-committed-per-second"></a>1 秒あたりのコミットされたトランザクション操作

カウンター名 : 1 秒あたりのコミットされたトランザクション操作。  
  
## <a name="description"></a>説明  

 1 秒あたりに、このサービスでコミットされたトランザクション操作の数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
