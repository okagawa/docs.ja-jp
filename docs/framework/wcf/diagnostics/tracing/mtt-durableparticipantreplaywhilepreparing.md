---
description: 詳細については、DurableParticipantReplayWhilePreparing を参照してください。
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fcaa50dd4faa548cad8ff085f1c66f94c63bd010
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635663"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing

WS-AT プロトコル サービスは、準備メッセージに応答していない永続的な参加要素から、リプレイ メッセージを受信しました。 そのため、トランザクションが中止されました。  
  
## <a name="description"></a>説明  

 永続的な参加要素がまだ準備している間にリプレイ メッセージが受信された場合は、トレースされます。 これは、この状態に対して無効なメッセージであり、トランザクションは中止されます。  
  
## <a name="troubleshooting"></a>トラブルシューティング

このエラーを受信すると、永続参加要素 (従属トランザクションマネージャーを含む) が障害から回復したことを示している可能性があります。ただし、トランザクションの結果が不明であるため、その状態を要求します。  
  
## <a name="see-also"></a>関連項目

- [トレース](index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../index.md)
