---
title: 重要なトレース
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: 9ad7c217b528cb2ad22169c1aea6391462bab1ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248671"
---
# <a name="significant-traces"></a>重要なトレース

このトピックでは、Windows Communication Foundation (WCF) によって生成される主なトレースの一部を示します。  
  
## <a name="significant-traces"></a>重要なトレース  
  
|Trace|Description|  
|-----------|-----------------|  
|Message Log トレース|トレースソースが有効になっているときに、メッセージログ機能によって WCF メッセージがログに記録されると、トレースが出力され `System.ServiceModel.MessageLogging` ます。 このトレースをクリックすると、メッセージが表示されます。 メッセージには、構成可能なログ ポイントが 4 つ (`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`) あり、これらは、メッセージ ログ トレースの Message Source 属性にも示されます。|  
|Message Received トレース|このトレースは、 `System.ServiceModel` トレースソースが情報レベルまたは詳細レベルで有効になっている場合に、WCF メッセージを受信したときに生成されます。 このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Message Sent トレース|このトレースは、 `System.ServiceModel` トレースソースが情報レベルまたは詳細レベルで有効になっている場合に、WCF メッセージが送信されるときに生成されます。 このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Get ChannelEndpointElement|このトレースは、情報レベルで Construct チャネル ファクトリに出力されます。 このトレースには、クライアントが対話しているエンドポイントの説明 (リモート アドレス、バインディング、コントラクト名など) が表示されます。|  
|Get ServiceElement|このトレースは、情報レベルで Construct サービス ホストに出力されます。 サービス コントラクトとバインディングの説明が提供されます。|  
|SocketConnection Create|このトレースは、クライアントによって実行される最初の "プロセス" アクションおよびサービスの "バイトを受信" アクティビティで出力されます。 ローカルとリモートの IP アドレスを提供します。 情報レベルで出力されます。|
