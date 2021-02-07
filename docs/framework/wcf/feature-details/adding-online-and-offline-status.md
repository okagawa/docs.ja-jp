---
description: オンラインとオフラインの状態の追加に関する詳細情報
title: オンライン ステータスとオフライン ステータスの追加
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 33f7920954ed28ebc2c3d34cc54a2e294f5730c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705240"
---
# <a name="adding-online-and-offline-status"></a>オンライン ステータスとオフライン ステータスの追加

多くの場合、アプリケーションではピア チャネル接続のステータスについて明確な詳細情報を監視することが重要です。 この情報は、`GetProperty` インターフェイスの実装で <xref:System.ServiceModel.IOnlineStatus> メソッドを呼び出すことで取得できます。 このインターフェイスを実装するオブジェクトは、接続ステータスを監視したり、`OnOnline` や `OnOffline` などのイベント ハンドラーを登録したりできるため、オンライン ステータスに変化があると即座に反応できます。  
  
 ピア チャネル インフラストラクチャでは、クライアントが少なくとも 1 つのピアに接続されているとオンラインと見なされ、そうでない場合はオフラインと見なされます。 このことは、開発中のアプリケーションをデバッグする際や、エンド ユーザーに詳細情報を表示する際に特に役立ちます。  
  
> [!NOTE]
> オンライン イベント ハンドラーでは、メッセージを送信する前に、まず、ノードが開いていることを確認する必要があります。  
  
## <a name="see-also"></a>関連項目

- [ピア チャネル アプリケーションの構築](building-a-peer-channel-application.md)
