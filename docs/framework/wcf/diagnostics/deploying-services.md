---
title: サービスの配置
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 07bd2a3938f238336dc00fa2e0826a28a9363a4a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294808"
---
# <a name="deploying-services"></a>サービスの配置

このトピックでは、Windows Communication Foundation (WCF) アプリケーションを実行時環境に配置する方法について説明します。  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a>アプリケーションのホスト環境の選択  

 WCF サービスは、マネージコードをサポートする任意の Windows プロセスで実行するように設計されています。 アクティブにするには、サービスを作成してそのコンテキストと有効期間を制御するランタイム環境内で、サービスをホストする必要があります。 ホスティング環境の範囲は、最も単純なコンソール アプリケーション内、Windows サービスやインターネット インフォメーション サービス (IIS) のようなサーバー環境、あるいは Windows アクティブ化サービス (WAS) で管理されるワーカー プロセス内での実行にまで及びます。 WCF アプリケーションのさまざまなホスティングオプションを確認するには、「 [ホスティングサービス](../hosting-services.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ホスティング](../feature-details/hosting.md)
- [ホスティング サービス](../hosting-services.md)
