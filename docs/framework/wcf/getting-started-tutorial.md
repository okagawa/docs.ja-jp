---
title: 'チュートリアル: Windows Communication Foundation アプリケーションの概要'
description: これらのチュートリアルでは、WCF アプリケーションの作成の概要について説明します。
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 620a83260f01e27a19b19227165695a621c88e5e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238237"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>チュートリアル: Windows Communication Foundation アプリケーションの概要

次の一連のチュートリアルでは、Windows Communication Foundation (WCF) のプログラミングエクスペリエンスを紹介します。 これらのチュートリアルを順番に実行すると、WCF アプリケーションの作成に必要な手順を理解することができます。 終了すると、実行中の WCF サービスと、サービスを呼び出す WCF クライアントが作成されます。

このチュートリアルでは、開発環境として Visual Studio を使用していることを前提としています。 別の開発環境を使用している場合は、Visual Studio 固有の手順を無視してください。

ダウンロードして実行できるサンプル WCF アプリケーションについては、 [Windows Communication Foundation のサンプル](samples/index.md)を参照してください。 サンプルの概要については、「 [作業の開始](samples/getting-started-sample.md)」のサンプルを参照してください。

サービスとクライアントの作成の詳細については、「 [基本的な WCF プログラミング](basic-wcf-programming.md)」を参照してください。

## <a name="wcf-tutorials"></a>WCF チュートリアル

最初の3つのチュートリアルでは、WCF サービスコントラクトの定義方法、実装方法、およびホスト方法について説明します。 作成したサービスは、コンソールアプリケーション内で自己ホストされます。 Microsoft インターネットインフォメーションサービス (IIS) でサービスをホストすることもできます。 詳細については、「 [How to: Host a WCF Service IN IIS](feature-details/how-to-host-a-wcf-service-in-iis.md)」を参照してください。 このチュートリアルではコードを使用してサービスを構成しますが、 [構成ファイル内でサービスを構成](configuring-services-using-configuration-files.md)することもできます。

- [チュートリアル: サービスコントラクトを定義する](how-to-define-a-wcf-service-contract.md)

    WCF コントラクトは、ユーザー定義のインターフェイスを使用して作成します。 このコントラクトは、サービスが公開する機能を定義します。

- [チュートリアル: サービスコントラクトを実装する](how-to-implement-a-wcf-contract.md)

    コントラクトを定義した後は、サービスクラスを使用して実装する必要があります。

- [チュートリアル: 基本的なサービスをホストして実行する](how-to-host-and-run-a-basic-wcf-service.md)

    サービスのエンドポイントを構成し、コンソールアプリケーションでサービスをホストします。 サービスがアクティブになるには、サービスを構成し、実行時環境内でホストする必要があります。 このランタイム環境では、サービスを作成し、そのコンテキストと有効期間を制御します。

次の2つのチュートリアルでは、サービスが公開する操作を呼び出すためにクライアントアプリケーションを作成、構成、および使用する方法について説明します。 サービスは、クライアント アプリケーションがサービスと通信するために必要な情報を定義したメタデータを公開します。 Visual Studio は、このメタデータにアクセスするプロセスを自動化し、それを使用してサービスのクライアントアプリケーションを構築します。 Visual Studio を使用しない場合は、 [ServiceModel メタデータユーティリティツール (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) を代わりに使用できます。

- [チュートリアル: クライアントを作成する](how-to-create-a-wcf-client.md)

    Wcf サービスから WCF クライアントプロキシを作成するためのメタデータを取得します。 メタデータを取得するには、Visual Studio を使用してサービス参照を追加するか、ServiceModel メタデータユーティリティツールを使用します。 サービスへのアクセスにクライアントが使用するエンドポイントを指定します。

- [チュートリアル: クライアントを使用する](how-to-use-a-wcf-client.md)

    WCF クライアントプロキシを使用して、サービス操作を呼び出します。

## <a name="reference"></a>関連項目

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>関連項目

- [概念の概要](conceptual-overview.md)
- [ドキュメントのガイド](guide-to-the-documentation.md)
- [Windows Communication Foundation とは](whats-wcf.md)
- [WCF 機能の詳細](feature-details/index.md)
- [基本的なプログラミングライフサイクル](basic-programming-lifecycle.md)
- [クライアントの構築](building-clients.md)
- [基本的な WCF プログラミング](basic-wcf-programming.md)
- [方法: 双方向コントラクトを作成する](feature-details/how-to-create-a-duplex-contract.md)
- [方法: 双方向コントラクトを使用してサービスにアクセスする](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [ServiceModel メタデータユーティリティツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [方法: Svcutil.exe を使用してメタデータドキュメントをダウンロードする](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [方法: 構成ファイルを使用してサービスのメタデータを公開する](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [バインドを使用したサービスとクライアントの構成](using-bindings-to-configure-services-and-clients.md)
- [作業の開始のサンプル](samples/getting-started-sample.md)
- [Windows Communication Foundation のサンプル](samples/index.md)
- [自己ホスト](samples/self-host.md)
