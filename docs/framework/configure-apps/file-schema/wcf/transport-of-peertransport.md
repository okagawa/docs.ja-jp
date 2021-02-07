---
description: 詳細については <transport> 、 <peerTransport>
title: <transport> の <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: ba3405c5dfadb513f92ebd537409a3f7b12fa291
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664510"
---
# <a name="transport-of-peertransport"></a>\<transport> の \<peerTransport>

このバインドで構成されたピアが送信する、セキュリティで保護されたメッセージのトランスポートの型を指定します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|credentialType|任意。 ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。 この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。|  
  
## <a name="credentialtype-attribute"></a>credentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|Certificate|ピア チャネル トランスポートの認証には X 509 証明書が必要です。|  
|Password|ピア チャネル トランスポートの認証には正しいパスワードが必要です。|  
  
### <a name="child-elements"></a>子要素  

 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|ピア トランスポートのセキュリティ設定を定義します。|  
  
## <a name="remarks"></a>解説  

 この要素は、の mode 属性 [\<security>](security-of-peertransport.md) がまたはに設定されている場合にのみ設定され `Transport` `TransportWithMessageCredential` ます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [トランスポートセキュリティ](../../../wcf/feature-details/transport-security.md)
- [トランスポート](../../../wcf/feature-details/transports.md)
- [トランスポートの選択](../../../wcf/feature-details/choosing-a-transport.md)
- [バインド](../../../wcf/bindings.md)
- [バインディングの拡張](../../../wcf/extending/extending-bindings.md)
- [カスタムバインド](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
