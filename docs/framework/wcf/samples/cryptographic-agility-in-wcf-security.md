---
description: 詳細については、「WCF セキュリティにおける暗号化の機敏性」を参照してください。
title: WCF セキュリティにおける暗号化の機敏性
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: ab46034b16a846f7399220480fc928655d931be0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778348"
---
# <a name="cryptographic-agility-in-wcf-security"></a>WCF セキュリティにおける暗号化の機敏性

このサンプルでは、標準/カスタムアルゴリズムでを指定して、Windows Communication Foundation (WCF) クライアントおよびサービスでの暗号化アジャイル実装を提供する方法を示します。 サンプルは、以下のプロジェクトで構成されます。

**サービス**

これは、インターフェイスを実装 `ICalculator` し、セキュリティで保護された <xref:System.ServiceModel.WSHttpBinding> セッションと信頼できるセッションを無効にしたを使用してエンドポイントをセキュリティで保護する、自己ホスト型 WCF サービスです。 このサービスは、カスタム `SecurityAlgorithmSuite` クラスを定義し、メッセージのセキュリティを確保するために使用される暗号化アルゴリズムを指定します。

**クライアント**

これは、認証が成功した後にサービスにアクセスする WCF クライアントです。 このクライアントは、`ICalculator` インターフェイスによって公開され、サービスによって実装される操作を呼び出します。 このクライアントも、同じカスタム `SecurityAlgorithmSuite` クラスを定義し、メッセージのセキュリティを確保するために使用される暗号化アルゴリズムを指定します。

## <a name="to-use-this-sample"></a>このサンプルを使用するには

1. Visual Studio 2012 で、CryptoAgility 性 .sln ソリューションを開きます。

2. Ctrl + Shift + B キーを押して、ソリューションをビルドします。

3. エクスプローラーを開き、\WCF\Basic\Security\CryptoAgility\Service\bin ディレクトリに移動し、[service.exe を右クリックして [ **管理者として実行**] を選択して、管理者特権で service.exe ファイルを実行します。

4. \WCF\Basic\Security\CryptoAgility\Client\bin ディレクトリに移動して、client.exe ファイルを通常の方法で実行します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>関連項目

- [Windows Communication Foundation セキュリティ](../feature-details/security.md)
