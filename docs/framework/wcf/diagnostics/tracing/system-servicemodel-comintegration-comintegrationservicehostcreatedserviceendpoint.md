---
description: 詳細については、「MsmqMoveOrDeleteAttemptFailed」を参照してください。
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 7b3c8dad9e3a3e88dff72706917f3729d55b3799
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769742"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed

メッセージを移動または削除できません。  
  
## <a name="description"></a>説明  

 このトレースは、MSMQ メッセージの移動、削除、または拒否の試行中にエラーが発生したことを示しています。  
  
 MSMQ メッセージは Windows Communication Foundation (WCF) によって採用されています (NetMsmqBinding または MsmqIntegrationBinding のいずれかと共に使用する場合)。このトレースは `ReceiveErrorHandling` 、NetMsmqBinding または MsmqIntegrationBinding で選択されたプロパティの値に関連しています。  
  
 このトレースはシステム全体についてのエラーを示すものではありません。 ただし、選択した有害メッセージの処置に失敗したことを示しています。 メッセージが有害になった場合の詳細、およびメッセージを適切に処理するようにサービスを構成する方法については、「 [有害メッセージの処理](../../feature-details/poison-message-handling.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [トレース](index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../index.md)
