---
title: 'エンドポイント: 1 秒あたりの失敗した呼び出し'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 0aeafa3d273ae22d9bbfe5e3edbac80c6e4851bd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271254"
---
# <a name="endpoint-calls-failed-per-second"></a>エンドポイント: 1 秒あたりの失敗した呼び出し

カウンター名 : 1 秒あたりの失敗した呼び出し。  
  
## <a name="description"></a>Description  

 未処理の例外を伴ってこのエンドポイントに到達した、1 秒あたりの呼び出しの回数。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 このカウンターは、このエンドポイントで未処理の例外が発生すると常にインクリメントされます。  
  
## <a name="see-also"></a>関連項目

- [コントラクトおよびサービスのエラーの指定と処理](../../specifying-and-handling-faults-in-contracts-and-services.md)
