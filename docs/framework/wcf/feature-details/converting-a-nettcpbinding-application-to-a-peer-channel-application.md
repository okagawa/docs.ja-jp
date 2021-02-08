---
description: '詳細: NetTcpBinding アプリケーションからピアチャネルアプリケーションへの変換'
title: NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 828ffce38fb05acff851c9fe5a6fbb38fffad6aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780415"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換

接続のパラメーターを記述するバインディングを使用して、WinFX を使用するクライアント間の接続を作成できます。 ピアツーピア接続を使用するように .NET Framework アプリケーションを変換するには、クライアント接続を行うときに、このテクノロジをサポートするバインディングが必要です。 ピア チャネルには、<xref:System.ServiceModel.NetPeerTcpBinding> と呼ばれるバインディングが用意されています。このバインディングは、<xref:System.ServiceModel.NetTcpBinding> と同じような方法で使用できます。 主な違いは、リゾルバー サービスの仕様とセキュリティ設定の定義です。  
  
 アプリケーションでリゾルバーとセキュリティの既定の設定を使用する場合、通常のクライアント/サーバー ベースのアプリケーションは、アプリケーションの構成ファイルでバインディング名を "NetTcpBinding" から "NetPeerTcpBinding" に変更するだけで、ピア チャネルを使用するように変換できます。アプリケーションのコード ベースを変更する必要はありません。  
  
## <a name="see-also"></a>関連項目

- [ピア チャネル アプリケーションの構築](building-a-peer-channel-application.md)
- [システム標準のバインディング](../system-provided-bindings.md)
