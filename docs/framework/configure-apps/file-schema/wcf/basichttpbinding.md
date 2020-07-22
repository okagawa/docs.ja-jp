---
title: <basicHttpBinding>
description: WS-I Basic Profile 1.1 に準拠したサービスと通信するために、WCF サービスがエンドポイントを構成および公開するために使用できるバインディングを定義します。
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: 5b2ce1973966468107d7aa4de545a976c67b13ed
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244024"
---
# \<basicHttpBinding>
ASMX ベースの Web サービスやクライアント、および WS-I Basic Profile 1.1 に準拠するその他のサービスとの通信が可能なエンドポイントを構成および公開するために、Windows Communication Foundation (WCF) サービスが使用できるバインドを表します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<basicHttpBinding>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="String" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`allowCookies`|クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定するブール値です。 既定値は、`false` です。<br /><br /> クッキーを使用する ASMX Web サービスと対話する場合にこのプロパティを使用できます。 この方法で、サーバーから返されるクッキーを、それ以降のサービスに対するすべてのクライアント要求に自動的にコピーできます。|  
|`bypassProxyOnLocal`|ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。 既定値は、`false` です。<br /><br /> インターネット リソースは、ローカル アドレスを持つ場合ローカルです。 ローカルアドレスは、同じコンピューター、ローカル LAN、またはイントラネット上にあり、構文的には、Uri とのようにピリオド (.) がないことで識別され `http://webserver/` `http://localhost/` ます。<br /><br /> この属性の設定は、BasicHttpBinding で構成されたエンドポイントがローカル リソースへのアクセス時にプロキシ サーバーを使用するかどうかを示します。 この属性が `true` の場合、ローカル インターネット リソースへの要求はプロキシ サーバーを使用しません。 この属性を `true` に設定した場合で、同じコンピューター上のサービスと対話するクライアントがプロキシを経由するときは、(localhost ではなく) ホスト名を使用します。<br /><br /> この属性が `false` の場合、すべてのインターネット要求はプロキシ サーバー経由で行われます。|  
|`closeTimeout`|クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|`hostNameComparisonMode`|URI の解析に使用する HTTP ホスト名比較モードを指定します。 この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。 既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。|  
|`maxBufferPoolSize`|チャネルからメッセージを受け取るメッセージ バッファーのマネージャーが使用するために割り当てられる、最大メモリ量を指定する整数値。 既定値は 524288 (0x80000) バイトです。<br /><br /> バッファー マネージャーは、バッファー プールを使用することで、バッファーの使用コストを最小化します。 バッファーは、チャネルから出てくるメッセージをサービスが処理するときに必要です。 メッセージの読み込み処理に十分なメモリがバッファー プールにない場合、バッファー マネージャーは、CLR ヒープから追加のメモリを割り当てる必要があります。これにより、ガベージ コレクションのオーバーヘッドが増加します。 CLR ガベージ ヒープから多大な割り当てが行われることは、バッファー プール サイズが小さすぎること、およびこの属性で指定される制限を緩めて割り当てを増やすとパフォーマンスが向上する可能性があることを示します。|  
|`maxBufferSize`|このバインディングで構成されるエンドポイントのメッセージが処理されるときのメッセージを格納するバッファーの最大サイズを指定する整数値 (バイト単位)。 既定値は 65,536 バイトです。|  
|`maxReceivedMessageSize`|このバインディングで構成されるチャネルが受信可能なメッセージの最大メッセージ サイズ (ヘッダーを含む) をバイト単位で定義する正の整数。 受信側のメッセージが大きすぎると、送信側は SOAP エラーを受け取ります。 メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。 既定値は 65,536 バイトです。|  
|`messageEncoding`|SOAP メッセージのエンコードに使用されるエンコーダーを定義します。 有効な値は次のとおりです。<br /><br /> -Text: テキストメッセージエンコーダーを使用します。<br />-Mtom: メッセージ伝送組織機構 1.0 (MTOM) エンコーダーを使用します。<br /><br /> 既定値は Text です。 この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。|  
|`name`|バインディングの構成名を格納する文字列です。 この値は、同じ型のバインド間で一意である必要があります。 .NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。 既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。|  
|`openTimeout`|実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|`proxyAddress`|HTTP プロキシのアドレスを格納する URI。 `useSystemWebProxy` が `true` に設定されている場合、この設定は `null` である必要があります。 既定値は、`null` です。|  
|`receiveTimeout`|受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:10:00 です。|  
|`sendTimeout`|送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|`textEncoding`|バインディングでメッセージの発行に使用される文字セット エンコーディングを設定します。 有効な値は次のとおりです。<br /><br /> -BigEndianUnicode: Unicode BigEndian エンコード。<br />-Unicode:16 ビットエンコード。<br />-UTF8: 8 ビットエンコーディング<br /><br /> 既定値は UTF8 です。 この属性は <xref:System.Text.Encoding> 型です。|  
|`transferMode`|要求または応答に対してメッセージがバッファーされるか、ストリーム配信されるかを指定する有効な <xref:System.ServiceModel.TransferMode> 値。|  
|`useDefaultWebProxy`|使用できる場合にシステムの自動設定 HTTP プロキシを使用するかどうかを指定するブール値。 既定値は、`true` です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|バインディングのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement> 型です。|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。 この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。|  
  
## <a name="remarks"></a>Remarks  
 BasicHttpBinding では、SOAP 1.1 メッセージを送信するために、HTTP をトランスポートとして使用します。 サービスは、ASMX クライアントが消費するエンドポイントなど、WS-I BP 1.1 に準拠するエンドポイントを開示するためにこのバインディングを使用できます。 同様に、クライアントは BasicHttpBinding を使用して、ASMX Web サービスや BasicHttpBinding で構成されるサービスなどの WS-I BP 1.1 に準じるエンドポイントを公開するサービスと通信できます。  
  
 既定ではセキュリティはオフになっていますが、子要素の mode 属性 [\<security>](security-of-basichttpbinding.md) を以外の値に設定することもでき `None` ます。 サービスは、"Text" メッセージ エンコードおよび UTF-8 テキスト エンコードを既定で使用します。  
  
## <a name="example"></a>例  
 第 1 世代と第 2 世代の Web サービスで HTTP 通信と最大限の相互運用性を実現する、<xref:System.ServiceModel.BasicHttpBinding> の使用例を次に示します。 バインディングは、クライアントとサービスの構成ファイルに指定されます。 バインディングの種類は、`binding` 要素の `<endpoint>` 属性を使用して指定します。 基本的なバインディングを構成してその設定の一部を変更する場合は、バインド構成を定義する必要があります。 エンドポイントは、`bindingConfiguration` 要素の `<endpoint>` 属性を使用して、名前でバインディング構成を参照する必要があります。次のサービスの構成コードを参照してください。  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a>例  
 .NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。 前の例の機能は、エンドポイントアドレスから bindingConfiguration を削除し、バインドから名前を削除することで実現できます。  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [バインド](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
