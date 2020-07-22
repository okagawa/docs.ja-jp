---
title: <behavior> の <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 489678a5adeae3965acae90a847c4b087478354d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140813"
---
# <a name="behavior-of-endpointbehaviors"></a>\<behavior> の \<endpointBehaviors>
エンドポイントの動作設定のコレクションを含む `behavior` 要素。 各動作には、それぞれの `name` によってインデックスが付けられます。 エンドポイントは、この名前を使用して各動作にリンクできます。 .NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。 既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|動作の構成名を含む一意の文字列。 この値は、要素の識別文字列として機能するため、一意のユーザー定義の文字列である必要があります。 .NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。 既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|Description|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|サービスに対するクライアントの認証に使用される資格情報を指定します。|  
|[\<callbackDebug>](callbackdebug.md)|Windows Communication Foundation (WCF) コールバックオブジェクトのサービスデバッグを指定します。|  
|[\<callbackTimeouts>](callbacktimeouts.md)|クライアント コールバックのタイムアウトを指定します。|  
|[\<clientVia>](clientvia.md)|メッセージの経路を指定します。|  
|[\<dataContractSerializer>](datacontractserializer.md)|DataContractSerializer 用の構成データが含まれています。|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|サービスが非同期に応答を返すことができるようにするエンドポイントの動作を指定します。|  
|[\<enableWebScript>](enablewebscript.md)|ASP.NET AJAX Web ページからサービスを使用できるようにするエンドポイントの動作を有効にします。 動作は、 \<webHttpBinding> 標準バインディングまたはバインディング要素と組み合わせて使用する必要があり \<webMessageEncoding> ます。|  
|[\<endpointDiscovery>](endpointdiscovery.md)|エンドポイントのさまざまな探索設定を指定します (探索可能性、スコープ、メタデータに対するカスタム拡張など)。|  
|[\<soapProcessing>](soapprocessing.md)|異なるバインディングの種類およびメッセージ バージョンの間でメッセージのマーシャリングに使用されるクライアント エンドポイントの動作を定義します。|  
|[\<synchronousReceive>](synchronousreceive-element.md)|サービスまたはクライアント アプリケーションでメッセージを受信する場合のランタイム動作を指定します。 属性や子要素はありません。|  
|[\<transactedBatching>](transactedbatching.md)|受信操作でトランザクション バッチがサポートされるかどうかを指定します。|  
|[\<webHttp>](webhttp.md)|構成によってエンドポイントに WebHttpBehavior を指定します。 この動作は、標準バインディングと組み合わせて使用すると \<webHttpBinding> 、WCF サービスの Web プログラミングモデルを有効にします。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|Description|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|エンドポイント動作要素のコレクション。|
