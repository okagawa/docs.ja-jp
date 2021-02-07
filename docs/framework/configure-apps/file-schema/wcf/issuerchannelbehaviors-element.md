---
description: '詳細情報: <issuerChannelBehaviors> 要素'
title: <issuerChannelBehaviors> 要素
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: 6be79f2ee6afb442a7a399ce49df4ad59dff2db5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725546"
---
# <a name="issuerchannelbehaviors-element"></a>\::: なし ( <issuerChannelBehaviors> )::: 要素

指定されたサービストークンサービスとの通信時に使用される Windows Communication Foundation (WCF) クライアントエンドポイントの動作 (構成で定義されている) のコレクションを格納します。 定義された動作には、: [ \: : no loc ( <clientCredentials> ):::](clientcredentials.md)要素を含めることはできません。

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\::: no loc (<System.servicemodel>):::](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\::: no loc ( <behaviors> ):::](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: no loc ( <endpointBehaviors> ):::](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: no loc ( <behavior> ):::](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: no loc ( <clientCredentials> ):::](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: no loc ( <issuedToken> ):::](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\::: no loc ( <issuerChannelBehaviors> ):::

## <a name="syntax"></a>構文

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

なし。

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|コレクションに動作を追加します。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[\::: no loc ( <issuedToken> ):::](issuedtoken.md)|サービスに対するクライアントの認証に使用されるカスタム トークンを指定します。|

## <a name="remarks"></a>解説

この要素を使用するのは、なんらかの動作 (`<clientCredentials>` 要素を含む動作以外) を使用してサービスと通信する必要がある場合です。 たとえば、 [ \: :: no loc ( <dataContractSerializer> ):](datacontractserializer-element.md) :: behavior 要素を含める必要がある場合です。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [サービス ID と認証](../../../wcf/feature-details/service-identity-and-authentication.md)
- [セキュリティ動作](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [フェデレーションと発行済みトークン](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
- [クライアントのセキュリティ保護](../../../wcf/securing-clients.md)
- [方法: フェデレーション クライアントを作成する](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [方法: ローカル発行者を設定する](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [フェデレーションと発行済みトークン](../../../wcf/feature-details/federation-and-issued-tokens.md)
