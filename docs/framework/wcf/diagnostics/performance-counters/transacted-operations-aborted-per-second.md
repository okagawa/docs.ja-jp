---
description: '詳細情報: 1 秒あたりの中断されたトランザクション操作'
title: 1 秒あたりの中止されたトランザクション操作
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: de130c18e065e48ed7ac18442b2bc5f82c2f6861
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771198"
---
# <a name="transacted-operations-aborted-per-second"></a>1 秒あたりの中止されたトランザクション操作

カウンター名 : 1 秒あたりの中止されたトランザクション処理数。  
  
## <a name="description"></a>説明  

 1 秒あたりに、このサービスで中止されたトランザクション処理の数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
