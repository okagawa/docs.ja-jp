---
description: 詳細については、「PeerFlooderReceiveMessageQuotaExceeded」を参照してください。
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 8ad164b253491f3a533c4828cd76f915eb5aed68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780870"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a>System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded

メッセージの受信速度が速すぎます。  
  
## <a name="description"></a>説明  

 このトレースは、受信メッセージの処理を試みたときに行われます。 特定の近隣ノードでクォータ セットが超過しているため、メッセージをその近隣ノードに転送できません。 応答しない近隣ノードが、メッセージ保留のバックログをクリアできなかった場合にこの状態が発生します。  
  
## <a name="troubleshooting"></a>トラブルシューティング  

 メッシュ内でメッセージが送信される速度を遅くしてください。  
  
## <a name="see-also"></a>関連項目

- [トレース](index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../index.md)
