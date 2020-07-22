---
title: <transport> の <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: b975015a9c9a0af53117900c45d917ce1c1a53e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732814"
---
# <a name="transport-of-nethttpbinding"></a>\<transport> の \<netHttpBinding>
HTTP トランスポートの認証パラメーターを制御するプロパティを定義します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|clientCredentialType|-HTTP 認証を使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。  既定値は、`None` です。 この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。|  
|proxyCredentialType|-HTTP 経由のプロキシを使用してドメイン内からクライアント認証を実行するときに使用される資格情報の種類を指定します。 この属性は、親 `mode` 要素の `security` 属性が `Transport` または `TransportCredentialsOnly` の場合にだけ適用されます。 この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。|  
|realm|ダイジェストまたは基本認証の HTTP 認証方式によって使用されるレルムを指定する文字列。 既定値は空の文字列です。|  
|policyEnforcement|この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。<br /><br /> 1. never –ポリシーは適用されません (拡張保護は無効になります)。<br />2. WhenSupported –ポリシーは、クライアントが拡張保護をサポートしている場合にのみ適用されます。<br />3. always –ポリシーは常に適用されます。 拡張保護をサポートしていないクライアントは認証に失敗します。|  
|protectionScenario|この列挙体は、ポリシーによって適用される保護シナリオを指定します。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|メッセージは、転送中はセキュリティで保護されません。|  
|Basic|基本認証を指定します。|  
|ダイジェスト|ダイジェスト認証を指定します。|  
|Ntlm|Windows 認証に失敗した場合で可能な場合は、NTLM 認証を指定します。|  
|Windows|Windows 統合認証を指定します。|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|-メッセージは、転送中にセキュリティ保護されません。|  
|Basic|RFC 2617 『HTTP Authentication: Basic and Digest Authentication』で定義されているとおりに基本認証を指定します。|  
|ダイジェスト|RFC 2617 『HTTP Authentication: Basic and Digest Authentication』で定義されているとおりにダイジェスト認証を指定します。|  
|Ntlm|Windows 認証に失敗した場合で可能な場合は、NTLM 認証を指定します。|  
|Windows|Windows 統合認証を指定します。|  
|Certificate|証明書を使用したクライアント認証を実行します。 このオプションは、親要素の `Mode` の `security` 属性が Transport に設定されている場合のみ機能し、TransportCredentialOnly に設定されている場合は機能しません。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|Description|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|のセキュリティ機能を定義 [\<netHttpBinding>](nethttpbinding.md) します。|  
  
## <a name="example"></a>例  
 基本的なバインディングを使用した SSL トランスポート セキュリティの使用例を次に示します。 既定で、基本的なバインディングは HTTP 通信をサポートします。  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
- [バインド](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
