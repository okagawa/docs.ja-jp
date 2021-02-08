---
description: 詳細については、「MsmqMessageDropped」を参照してください。
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 41b9c6d5399f0f6b458404ee4b64624e5863c777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780961"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped

MSMQ はメッセージを破棄しました。  
  
## <a name="description"></a>説明  

 このトレースは、MSMQ メッセージが破棄されたことを示します。 MSMQ メッセージは Windows Communication Foundation (WCF) (NetMsmqBinding または MsmqIntegrationBinding で使用) が処理できない場合に削除できます。 このようなメッセージは、有害メッセージと呼ばれます。  
  
 有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Drop` に設定されていると破棄されます。 破棄されたメッセージはキューから削除され、元に戻すことはできません。  
  
 メッセージが有害になった場合の詳細、およびメッセージを適切に処理するようにサービスを構成する方法については、「 [有害メッセージの処理](../../feature-details/poison-message-handling.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [トレース](index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../index.md)
- [有害メッセージの処理](../../feature-details/poison-message-handling.md)
