---
description: '詳細情報: 重要なトレース'
title: 重要なトレース
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: 6d3e12c82312c2a8a3f0a19b4dc50e99e21b9730
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635546"
---
# <a name="significant-traces"></a>重要なトレース

このトピックでは、Windows Communication Foundation (WCF) によって生成される主なトレースの一部を示します。  
  
## <a name="significant-traces"></a>重要なトレース  
  
|Trace|説明|  
|-----------|-----------------|  
|Message Log トレース|トレースソースが有効になっているときに、メッセージログ機能によって WCF メッセージがログに記録されると、トレースが出力され `System.ServiceModel.MessageLogging` ます。 このトレースをクリックすると、メッセージが表示されます。 メッセージには、構成可能なログ ポイントが 4 つ (`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`) あり、これらは、メッセージ ログ トレースの Message Source 属性にも示されます。|  
|Message Received トレース|このトレースは、 `System.ServiceModel` トレースソースが情報レベルまたは詳細レベルで有効になっている場合に、WCF メッセージを受信したときに生成されます。 このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Message Sent トレース|このトレースは、 `System.ServiceModel` トレースソースが情報レベルまたは詳細レベルで有効になっている場合に、WCF メッセージが送信されるときに生成されます。 このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Get ChannelEndpointElement|このトレースは、情報レベルで Construct チャネル ファクトリに出力されます。 このトレースには、クライアントが対話しているエンドポイントの説明 (リモート アドレス、バインディング、コントラクト名など) が表示されます。|  
|Get ServiceElement|このトレースは、情報レベルで Construct サービス ホストに出力されます。 サービス コントラクトとバインディングの説明が提供されます。|  
|SocketConnection Create|このトレースは、クライアントによって実行される最初の "プロセス" アクションおよびサービスの "バイトを受信" アクティビティで出力されます。 ローカルとリモートの IP アドレスを提供します。 情報レベルで出力されます。|
