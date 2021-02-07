---
description: 詳細については、「ServiceHost とサービスモデルレイヤーの拡張」を参照してください。
title: ServiceHost とサービス モデル レイヤーの拡張
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: 446c02fbbb2391a4cc9c08c9e42f2194dfbcf9b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735063"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>ServiceHost とサービス モデル レイヤーの拡張

サービス モデル レイヤーには、基になるチャネルから受信メッセージを取得し、そのメッセージをアプリケーション コードでのメソッド呼び出しに変換し、結果を呼び出し元に送信するという役割があります。 サービス モデル拡張は、クライアントやディスパッチャーの機能、カスタム動作、メッセージとパラメーターの途中受信、およびその他の拡張機能に関連する実行や通信の動作と機能を変更または実装します。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [クライアントの拡張](extending-clients.md)  
 クライアント ランタイムを途中受信して変更できるインターフェイス、およびクライアント アプリケーションのカスタム拡張を挿入できるクラスについて説明します。 たとえば、カスタム クライアント メッセージ ログやカスタム メッセージ シリアル化などを実行できます。  
  
 [ディスパッチャーの拡張](extending-dispatchers.md)  
 サービス ランタイムを途中受信して変更できるインターフェイス、およびサービス アプリケーションのカスタム拡張を挿入できるクラスについて説明します。 たとえば、カスタム サービス ログ、サービス側でのメッセージ検証、カスタム ディスパッチなどを実行できます。  
  
 [拡張可能オブジェクト](extensible-objects.md)  
 5 つの拡張可能オブジェクトと、<xref:System.ServiceModel.IExtensibleObject%601> パターンについて説明します。 拡張可能オブジェクト パターンは、既存のランタイム クラスに新しい機能を付加して拡張したり、オブジェクトに新しい状態を追加するために使用します。 このようなオブジェクトを実際に拡張することにより、処理の段階に応じて、共通の拡張可能オブジェクトに定義された共有の状態や機能にアクセスすることができます。  
  
 [動作を使用したランタイムの構成と拡張](configuring-and-extending-the-runtime-with-behaviors.md)  
 WCF ランタイムで設定を変更したり拡張機能を挿入したりするには、ビヘイビアーを使用します。 WCF には、調整機能、インスタンス化、およびサービスと操作に関するその他のさまざまな側面を制御するための、システムに実装済みの動作が用意されています。 ここでは、独自のカスタム動作を作成し、プログラムおよび構成ファイルにより、作成したカスタム動作を使用できるようにする方法について説明します。  
  
 [ServiceHostFactory を使用したホストの拡張](extending-hosting-using-servicehostfactory.md)  
 <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> および <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> を拡張し、<xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> クラスを使用してホスト環境をカスタマイズする方法について説明します。  
  
## <a name="reference"></a>関連項目  
  
## <a name="related-sections"></a>関連項目
