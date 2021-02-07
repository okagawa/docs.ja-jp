---
description: 詳細については <security> 、 <webHttpBinding>
title: <security> の <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: a80a919ef877f01503e5ceaeb4fe7432e46f288c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683048"
---
# <a name="security-of-webhttpbinding"></a>\<security> の \<webHttpBinding>

で構成されるエンドポイントのセキュリティ要件を指定し [\<webHttpBinding>](webhttpbinding.md) ます。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|mode|トランスポート レベルのセキュリティをエンドポイントで使用するか、セキュリティを使用しないかを指定します。 既定値は、`None` です。 この属性は <xref:System.ServiceModel.WebHttpSecurityMode> 型です。|  
  
## <a name="mode-attribute"></a>Mode 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|セキュリティを無効にします。|  
|トランスポート|セキュリティは、HTTPS を使用して確保されます。 サービスは、SSL 証明書を使用して構成する必要があります。 メッセージは、HTTPS およびサービスを使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。 クライアント認証は、の属性によって制御され `ClientCredentialType` [\<transport>](transport-of-webhttpbinding.md) ます。|  
|TransportCredentialOnly|このモードは、メッセージの整合性と機密性を提供しません。 HTTP ベースのクライアント認証を提供します。 このモードを使用するときは、十分に注意する必要があります。 トランスポートセキュリティが他の方法 (IPSec など) によって提供され、WCF インフラストラクチャによってクライアント認証のみが提供される環境で使用する必要があります。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|トランスポートのセキュリティ設定を定義します。 この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|SOAP メッセージではなく HTTP 要求に応答する Windows Communication Foundation (WCF) Web サービスのエンドポイントを構成するために使用されるバインド要素。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
- [資格情報の種類の選択](../../../wcf/feature-details/selecting-a-credential-type.md)
- [バインド](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [WCF Web HTTP プログラミング モデル](../../../wcf/feature-details/wcf-web-http-programming-model.md)
