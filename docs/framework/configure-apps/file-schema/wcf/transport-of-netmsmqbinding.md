---
title: <transport> の <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152932"
---
# <a name="transport-of-netmsmqbinding"></a>\<transport> の \<netMsmqBinding>
トランスポートのセキュリティ設定を定義します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|msmqAuthenticationMode|MSMQ トランスポートによるメッセージの認証方法を指定します。 有効な値は次のとおりです。<br /><br /> -None: 認証なし。<br />-WindowsDomain: 認証メカニズムは Active Directory を使用して、メッセージに関連付けられているセキュリティ識別子の x.509 証明書を取得します。 次に、これを使用してキューの ACL がチェックされ、ユーザーがキューへの書き込み権限を持っていることが確認されます。<br />-Certificate: チャネルは、証明書ストアから証明書を取得します。<br /><br /> 既定値は、`WindowsDomain` です。<br /><br /> この属性が `None` に設定されている場合、`msmqProtectionLevel` 属性も `None` に設定する必要があります。 この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。|  
|msmqEncryptionAlgorithm|メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。 有効な値は次のとおりです。<br /><br /> - RC4Stream<br />-AES<br />-既定値は `RC4Stream` です。 この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。|  
|msmqProtectionLevel|MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。 暗号化を行うとメッセージの整合性が確保されますが、署名および暗号化を使用するとメッセージの整合性と否認防止の両方が確保されます。 つまり、実際には送信者から送信されたメッセージであり、送信者はその人物であると言います。 有効な値は次のとおりです。<br /><br /> -None: 保護がありません。<br />-Sign: メッセージは署名されています。<br />-EncryptAndSign: メッセージは暗号化され、署名されます。<br />-既定値は `Sign` です。|  
|msmqSecureHashAlgorithm|メッセージ ダイジェストの計算に使用されるハッシュ アルゴリズムを指定します。 有効な値は次のとおりです。<br /><br /> -MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> 既定値は、`SHA1` です。 この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。<br>MD5 と SHA1 の衝突の問題のため、SHA256 以上をお勧めします。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|Description|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|キューに置かれているトランスポートのセキュリティ設定を定義します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [WCF のキュー](../../../wcf/feature-details/queues-in-wcf.md)
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
- [バインド](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
