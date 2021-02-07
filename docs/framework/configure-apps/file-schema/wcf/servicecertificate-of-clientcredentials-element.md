---
description: '詳細については、次を参照してください: <serviceCertificate> of <clientCredentials> 要素'
title: <serviceCertificate><clientCredentials>要素の
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 5503c1a60b2d37f4f9359a2f49c019c37df71619
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682905"
---
# <a name="servicecertificate-of-clientcredentials-element"></a>\<serviceCertificate>\<clientCredentials>要素の

クライアントに対してサービスを認証する際に使用される証明書を指定します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|ネゴシエーション プロトコル経由でサービスまたは STS が証明書を提供しないときに使用される X.509 証明書を指定します。|  
|[\<scopedCertificates>](scopedcertificates-element.md)|認証用の (範囲指定された) 特定のサービスにより提供される X.509 証明書のコレクションを表します。 このコレクションは一般に、フェデレーション シナリオでセキュリティ トークン サービスのサービス証明書を指定するために使用されます。|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|クライアントで使用されるサービス証明書の認証動作を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|サービスに対するクライアント自身の認証のためにクライアントによって使用される資格情報を指定します。|  
  
## <a name="remarks"></a>解説  

 この構成要素は、SSL 認証を使用してサービスから提示された証明書を検証するためにクライアントが使用する設定を指定します。 また、このクラスには、メッセージ セキュリティを使用してサービスへのメッセージを暗号化するためにクライアントで明示的に構成される、サービスの証明書も含まれます。  
  
 要素の属性 `serviceCertificate` は、の属性と同じです [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md) 。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [セキュリティ動作](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [クライアントのセキュリティ保護](../../../wcf/securing-clients.md)
- [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
