---
description: '詳細情報: エンドポイント: 1 秒あたりの承認されていないセキュリティ呼び出し'
title: 'エンドポイント : 1 秒あたりの承認されていないセキュリティ呼び出し'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 55a49091426538304aceda52308e3f8df2010d6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655462"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>エンドポイント : 1 秒あたりの承認されていないセキュリティ呼び出し

カウンター名 : 1 秒あたりの承認されていないセキュリティ呼び出し。  
  
## <a name="description"></a>説明  

 有効なユーザーから適切な保護を適用して送信されたが、特定のタスクの実行がユーザーに許可されていない、受信メッセージの 1 秒あたりの数です。  
  
 このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
