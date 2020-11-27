---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 12978af11ac3663403deaeb21818643ca2d366aa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260358"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected

MSMQ はメッセージを拒否しました。  
  
## <a name="description"></a>Description  

 このトレースは、MSMQ メッセージが拒否されたことを示します。  
  
 MSMQ メッセージは、Windows Communication Foundation (WCF) (NetMsmqBinding または MsmqIntegrationBinding で使用される) が処理できない場合に拒否されることがあります。 このようなメッセージは、有害メッセージと呼ばれます。 有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると拒否されます。 拒否されたメッセージは、送信側の [配信不能キュー](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)に配信されます。  
  
 メッセージが有害になった場合の詳細、およびメッセージを適切に処理するようにサービスを構成する方法については、「 [有害メッセージの処理](../../feature-details/poison-message-handling.md)」を参照してください。  
  
 MSMQ での拒否されたメッセージの意味の詳細については、「 [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [トレース](index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../index.md)
- [有害メッセージの処理](../../feature-details/poison-message-handling.md)
- [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))
