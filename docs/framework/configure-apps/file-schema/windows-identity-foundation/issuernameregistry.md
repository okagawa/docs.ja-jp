---
description: '詳細情報: <issuerNameRegistry>'
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 73eb0d9d4d19f8e25f2db501e8cb3858d346ac2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803855"
---
# \<issuerNameRegistry>

トークンハンドラーコレクションのハンドラーによって使用される発行者名レジストリを構成します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|type|クラスから派生する型 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。 カスタムを指定する方法の詳細については `type` 、「[カスタム型参照]」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|属性で `type` 構成ベースの発行者名レジストリ (クラス) を指定する場合は、 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> [\<trustedIssuers>](trustedissuers.md) 要素を指定する必要があります。 [\<trustedIssuers>](trustedissuers.md)要素は `<add>` 、 `<clear>` `<remove>` 子要素として、、またはの各要素を受け取ることができます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|セキュリティトークンハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>解説  

 発行者のトークンはすべて、発行者名レジストリを使用して検証されます。 これは、クラスから派生するオブジェクトです <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。 発行者名レジストリは、対応する発行者によって生成されるトークンの署名を検証するために必要な暗号マテリアルにニーモニック名を関連付けるために使用されます。 発行者名レジストリは、証明書利用者 (RP) アプリケーションによって信頼されている発行者の一覧を保持します。 発行者名レジストリの種類は、属性を使用して指定され `type` ます。 要素は、 `<issuerNameRegistry>` 指定された型の構成を提供する1つ以上の子要素を持つことができます。 これらの子要素を処理するロジックは、メソッドをオーバーライドすることによって指定し <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> ます。  
  
 WIF では、単一の発行者名のレジストリの種類が、クラスのすぐに使用 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> できます。 このクラスは、構成で指定された信頼された発行者証明書のセットを使用します。 これには、 `<trustedIssuers>` 信頼された発行元の証明書のコレクションを構成する子構成要素が必要です。 信頼された証明書は、asn.1 でエンコードされた証明書の拇印を使用して指定され、 `<add>` 、 `<clear>` 、または要素を使用してコレクションに追加または削除され `<remove>` ます。  
  
 `<issuerNameRegistry>`要素は、クラスによって表され <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> ます。  
  
> [!NOTE]
> 要素 `<issuerNameRegistry>` の子要素としての指定 [\<identityConfiguration>](identityconfiguration.md) は非推奨とされましたが、旧バージョンとの互換性のために引き続きサポートされています。 要素の設定は、要素の設定 `<securityTokenHandlerConfiguration>` よりも優先さ `<identityConfiguration>` れます。  
  
## <a name="example"></a>例  

 次の XML は、構成ベースの発行者名レジストリを指定する方法を示しています。  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
