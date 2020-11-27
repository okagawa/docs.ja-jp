---
title: 1 秒あたりのセキュリティ検証と認証エラー
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: c64c121550043127db674fac6287a870449d789d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253125"
---
# <a name="security-validation-and-authentication-failures-per-second"></a>1 秒あたりのセキュリティ検証と認証エラー

カウンター名 : 1 秒あたりのセキュリティ検証と認証エラー  
  
## <a name="description"></a>Description  

 このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。 この問題には、次のようなものがあります。  
  
- メッセージからクライアント トークンを読み取ることができない。  
  
- クライアント トークンが認証に失敗した (例 : 無効なパスワード)。  
  
- 署名の検証に失敗した (例 : メッセージが改ざんされた)。  
  
- メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。  
  
- 復号化に失敗した。  
  
- 一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。  
  
- TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。  
  
 このカウンターの種類は [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))で、次の式を使用して値が計算されます。  
  
 (N1-N0)/((D1-D0)/F)
