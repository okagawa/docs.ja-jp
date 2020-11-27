---
title: セキュリティの拡張
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: d91f4812dbccb7807be2e0780cccd1d0c38b1f40
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273062"
---
# <a name="extending-security"></a>セキュリティの拡張

新しい要求の種類とカスタムトークンに対応するために、Windows Communication Foundation (WCF) のセキュリティインフラストラクチャを拡張することができます。 このセクションの各トピックでは、この方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
 [カスタム資格情報と資格情報の検証](custom-credential-and-credential-validation.md)  
 カスタム資格情報の検証中に ID モデルを使用する方法について説明します。  
  
 [カスタム トークン](custom-tokens.md)  
 通常、セキュリティ トークン サービス (STS) から発行されるトークンは SAML トークンです。 ここでは、カスタムのトークンの種類を作成する方法について説明します。  
  
 [カスタム承認](custom-authorization.md)  
 カスタム承認を実装する方法について説明します。  
  
 [認証のためのサービスの ID のオーバーライド](overriding-the-identity-of-a-service-for-authentication.md)  
 認証のためにサービスの ID をオーバーライドする方法について説明します。  
  
 [方法: カスタム クライアント ID 検証機能を作成する](how-to-create-a-custom-client-identity-verifier.md)  
 カスタム エンドポイント ID を検証する方法について説明します。  
  
 [方法: 署名および暗号化に個別の X.509 証明書を使用する](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 通常、メッセージの署名および暗号化は 1 つの証明書を使用して行われます。 ここでは、必要に応じて 2 つの証明書を使用する方法について説明します。  
  
 [方法: X.509 証明書の秘密キーの暗号化プロバイダーを変更する](change-cryptographic-provider-x509-certificate-private-key.md)  
 X.509 証明書の秘密キーを提供するために使用される暗号化サービスプロバイダーを変更する方法と、プロバイダーを Windows Communication Foundation (WCF) フレームワークに統合する方法について説明します。  
  
## <a name="reference"></a>関連項目  

 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>関連項目  

 [Security](../feature-details/security.md)  
  
 [基本的な WCF プログラミング](../basic-wcf-programming.md)  
  
## <a name="see-also"></a>関連項目

- [セキュリティの概要](../feature-details/security-overview.md)
