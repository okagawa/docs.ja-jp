---
description: '詳細情報: <certificateReference>'
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 3404d44457849fb78ae88617d049a2199f2b5509
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681787"
---
# \<certificateReference>

証明書ストアの x.509 証明書を検索して検証するために使用する設定を指定します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|storeName|X.509 証明書ストアの名前。 既定値は "My" です。 任意。|  
|storeLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 証明書ストアの場所を示す値です。 既定値は "LocalMachine" です。 任意。|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>実行する検索の種類を示す値です。 既定値は "Findbysubjectdistinguishedname です" です。 任意。|  
|findValue|X.509 証明書ストアで検索する値。 任意。|  
|isChainIncluded|証明書チェーンを使用して検証を実行するかどうかを指定します。 既定値は "true" です。検証は、証明書チェーンを使用して実行されます。 任意。|  
  
### <a name="child-elements"></a>子要素  

 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|トークンの暗号化と復号化に使用される証明書を構成します。|  
  
## <a name="remarks"></a>解説  

 要素は、 `<certificateReference>` 証明書ストア内の x.509 証明書の検索と検証に使用される設定を指定します。 要素の子要素として指定されている場合は、 `<serviceCertificate>` トークンの暗号化と復号化に使用される x.509 証明書の場所と検証の設定を指定します。 `<certificateReference>`要素は、クラスによって表され <xref:System.ServiceModel.Configuration.CertificateReferenceElement> ます。
