---
description: '詳細については、「サービス: セキュリティ検証と認証エラー」を参照してください。'
title: 'サービス : セキュリティ検証と認証エラー'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 8938c74e706526a02bf2ea5885951d067d6ebae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759485"
---
# <a name="service-security-validation-and-authentication-failures"></a>サービス : セキュリティ検証と認証エラー

カウンター名 : セキュリティ検証と認証エラー  
  
## <a name="description"></a>説明  

 このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。 この問題には、次のようなものがあります。  
  
- メッセージからクライアント トークンを読み取ることができない。  
  
- クライアント トークンが認証に失敗した (例 : 無効なパスワード)。  
  
- 署名の検証に失敗した (例 : メッセージが改ざんされた)。  
  
- メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。  
  
- 復号化に失敗した。  
  
- 一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。  
  
- TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。
