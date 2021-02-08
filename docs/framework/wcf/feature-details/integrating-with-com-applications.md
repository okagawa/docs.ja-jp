---
description: 詳細については、「COM アプリケーションとの統合」を参照してください。
title: COM アプリケーションとの統合
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: 7afee4bed334d7f392b73773f0981022a59170fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802802"
---
# <a name="integrating-with-com-applications"></a>COM アプリケーションとの統合

WCF サービスモニカーを使用すると、Windows Communication Foundation (WCF) サービスを既存のコードに直接統合できます。 サービス モニカーは Office VBA、Visual Basic 6.0、または Visual C++ 6.0 などの幅広い COM ベースの開発環境で使用可能です。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [COM アプリケーションとの統合の概要](integrating-with-com-applications-overview.md)  
 統合プロセスの主要部分の概要を説明します。  
  
 [方法: サービス モニカーを登録および構成する](how-to-register-and-configure-a-service-moniker.md)  
 COM アプリケーション内で WCF サービスモニカーを使用するには、必要な属性型を COM に登録し、必要なバインド構成を使用して COM アプリケーションとモニカーを構成します。  
  
 [方法: 未登録で Windows Communication Foundation のサービス モニカーを使用する](use-the-wcf-service-moniker-without-registration.md)  
 WSDL (Web Services Definition Language) ドキュメントの形式で、または WS-MetadataExchange エンドポイントからコントラクトの定義を取得する方法を説明します。  
  
 [方法: WSDL コントラクトと共にサービス モニカーを使用する](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 Wcf WSDL モニカーを使用して WCF サンプルを呼び出す方法について説明します。  
  
 [方法: Metadata Exchange コントラクトと共にサービス モニカーを使用する](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 Mex エンドポイントを指定する WCF モニカーを使用して WCF サンプルを呼び出す方法について説明します。  
  
 [方法: チャネルのセキュリティ資格情報を指定する](how-to-specify-channel-security-credentials.md)  
 WCF サービスモニカーは、 `IChannelCredentials` チャネル資格情報を指定するためのさまざまな代替メソッドを許可するインターフェイスをサポートします。  
  
## <a name="reference"></a>関連項目  

 <xref:System.ServiceModel>  
  
## <a name="see-also"></a>関連項目

- [COM + アプリケーションとの統合](integrating-with-com-plus-applications.md)
