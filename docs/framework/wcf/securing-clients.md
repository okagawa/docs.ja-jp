---
title: クライアントのセキュリティ保護
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: b7f720b83a858c8739d2f7b9bf63d29c54b914e0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242254"
---
# <a name="securing-clients"></a>クライアントのセキュリティ保護

Windows Communication Foundation (WCF) では、サービスはクライアントのセキュリティ要件を決定します。 つまり、使用するセキュリティ モード、およびクライアントが資格情報を提供するかどうかは、サービスによって指定されます。 そのため、クライアントをセキュリティで保護するプロセスは、サービスから取得したメタデータ (公開されている場合) を使用してクライアントを構築するという簡単なものになります。 クライアントを構成する方法は、メタデータによって指定されます。 クライアントが資格情報を提供することをサービスが要求する場合、要件に適した資格情報を取得する必要があります。 ここでは、このプロセスについて詳しく説明します。 セキュリティで保護されたサービスの作成の詳細については、「 [サービスのセキュリティ保護](securing-services.md)」を参照してください。  
  
## <a name="the-service-specifies-security"></a>サービスによるセキュリティの指定  

 既定では、WCF バインドではセキュリティ機能が有効になっています。 (例外は <xref:System.ServiceModel.BasicHttpBinding> です)。このため、WCF を使用してサービスを作成した場合、認証、機密性、および整合性を確保するためにセキュリティを実装する可能性が高くなります。 この場合、サービスが提供するメタデータによって、セキュリティで保護された通信チャネルの確立に必要なものが示されます。 サービス メタデータにセキュリティ要件がまったく含まれていない場合には、サービスでセキュリティ スキーム (SSL (Secure Sockets Layer) over HTTP など) を強制する方法はありません。 ただし、サービスがクライアントに資格情報の提供を求める場合は、クライアントの開発者、展開担当者、または管理者は、クライアントがサービスに対して認証を受けるときに実際に使用する資格情報を提供する必要があります。  
  
## <a name="obtaining-metadata"></a>メタデータの取得  

 クライアントを作成する場合、最初の手順はクライアントが通信を行うサービスからメタデータを取得することです。 これは、次の 2 つの方法で行うことができます。 最初に、サービスが metadata exchange (MEX) エンドポイントを公開するか、または HTTP または HTTPS 経由でメタデータを使用できるようにする場合、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)を使用してメタデータをダウンロードできます。これにより、クライアントのコードファイルと構成ファイルの両方が生成されます。 (このツールの使用方法の詳細については、「 [WCF クライアントを使用したサービスへのアクセス](accessing-services-using-a-wcf-client.md)」を参照してください)。サービスが MEX エンドポイントを公開しておらず、そのメタデータを HTTP または HTTPS で使用できない場合は、サービスの作成者に、セキュリティ要件とメタデータについてのドキュメントを問い合わせる必要があります。  
  
> [!IMPORTANT]
> メタデータが信頼されたソースのものであり、改ざんされていないことを確認することをお勧めします。 HTTP プロトコルを使用して取得したメタデータはクリア テキストで送信されるため、改ざんされるおそれがあります。 サービスで <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> プロパティおよび <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> プロパティを使用している場合は、サービス作成者から提供された URL で、HTTPS プロトコルを使用してデータをダウンロードします。  
  
## <a name="validating-security"></a>セキュリティの検証  

 メタデータのソースは、信頼されたソースと信頼関係のないソースの 2 つに大きく分けられます。 ソースを信頼しており、そのソースのセキュリティで保護された MEX エンドポイントからクライアント コードとその他のメタデータをダウンロードしている場合、何の懸念もなく、クライアントをビルドし、適切な資格情報を提供して実行できます。  
  
 ただし、ほとんど未知のソースからクライアントとメタデータをダウンロードする場合は、コードで使用しているセキュリティ対策を検証する必要があります。 たとえば、サービスにより (最低でも) 機密性と整合性とが要求されていない場合は、個人情報や財務情報を送信するクライアントを作成するようなことは絶対に避けてください。 このような情報が表示されるため、サービスの所有者は、このような情報を開示する範囲に信頼する必要があります。  
  
 したがって、信頼できないソースから受け取ったコードとメタデータを使用する場合には、それがこちらの必要とするセキュリティ レベルを満たしていることを確認する必要があります。  
  
## <a name="setting-a-client-credential"></a>クライアント資格情報の設定  

 クライアントへの資格情報の設定には、次の 2 つの手順があります。  
  
1. サービスが必要とする *クライアント資格情報の種類* を決定します。 これは、2 つある方法のどちらかによって行います。 1 つ目の方法として、サービス作成者からドキュメントを入手している場合は、このドキュメントにサービスが要求するクライアント資格情報の種類が示されています (クライアント資格情報の種類が指定されている場合)。 2 番目の方法は Svcutil.exe ツールによって作成された構成ファイルしかない場合で、個々のバインディングを調べることで必要な資格情報の種類を特定できます。  
  
2. 実際のクライアント資格情報を指定します。 実際のクライアント資格情報は、型と区別するために *クライアント資格* 情報の値と呼ばれます。 たとえば、クライアント資格情報の種類として証明書が指定されている場合、サービスが信頼する証明機関によって発行された X.509 証明書を指定する必要があります。  
  
### <a name="determining-the-client-credential-type"></a>クライアント資格情報の種類の特定  

 Svcutil.exe ツールによって生成された構成ファイルがある場合は、セクションを調べて、 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) 必要なクライアント資格情報の種類を確認します。 このセクション内には、セキュリティ要件を指定するバインド要素があります。 具体的には、 \<security> 各バインドの要素を調べます。 この要素には `mode` 属性が含まれており、3 つの値のいずれか (`Message`、`Transport`、または `TransportWithMessageCredential`) に設定できます。 この属性の値によってモードが決定され、このモードによってどの子要素が有効なのかが決定されます。  
  
 `<security>`要素には、要素または要素のいずれか `<transport>` `<message>` 、またはその両方を含めることができます。 セキュリティ モードと一致する要素が有効な要素です。 たとえば、次のコードでは、セキュリティ モードを `"Message"`、`<message>` 要素のクライアント資格情報の種類を `"Certificate"` に指定しています。 この場合、`<transport>` 要素は無視できます。 ただし、`<message>` 要素で X.509 証明書を提示する必要があることが指定されています。  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"
                      realm="" />  
           <message clientCredentialType="Certificate"
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 次の例に示すように、`clientCredentialType` 属性が `"Windows"` に設定されている場合は、実際の資格情報の値を指定する必要はありません。 これは、Windows 統合セキュリティでは、クライアントを実行しているユーザーの実際の資格情報 (Kerberos トークン) が提供されるためです。  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>クライアント資格情報の値の設定  

 クライアントが資格情報を提供する必要があると特定された場合は、クライアントを構成する適切なメソッドを使用します。 たとえば、クライアント証明書を設定するには、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> メソッドを使用します。  
  
 X.509 証明書は広く使用されている資格情報の形式です。 資格情報は次の 2 つの方法で提供できます。  
  
- クライアント コードで (`SetCertificate` メソッドを使用して) プログラミングする方法。  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)次に示すように、クライアントの構成ファイルのセクションを追加し、要素を使用し `clientCredentials` ます。  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>\<clientCredentials>コード内での値の設定  

 コードに値を設定するには、 [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) クラスのプロパティにアクセスする必要があり <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> ます。 このプロパティは、次の表に示すように、各種の資格情報の種類にアクセスできる <xref:System.ServiceModel.Description.ClientCredentials> オブジェクトを返します。  
  
|ClientCredential プロパティ|説明|メモ|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> を返します|クライアントがサービスに対して自身を認証するために提供する X.509 証明書を表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|<xref:System.ServiceModel.Security.HttpDigestClientCredential> を返します|HTTP ダイジェスト資格情報を表します。 この資格情報は、ユーザー名とパスワードのハッシュです。|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|<xref:System.ServiceModel.Security.IssuedTokenClientCredential> を返します|フェデレーション シナリオで通常使用される、セキュリティ トークン サービスによって発行されるカスタム セキュリティ トークンを表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|<xref:System.ServiceModel.Security.PeerCredential> を返します|Windows ドメインのピア メッシュに参加するためのピア資格情報を表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> を返します|帯域外ネゴシエーションでサービスによって提供される X.509 証明書を表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential> を返します|ユーザー名とパスワードのペアを表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|<xref:System.ServiceModel.Security.WindowsClientCredential> を返します|Windows クライアントの資格情報 (Kerberos 資格情報) を表します。 このクラスのプロパティは読み取り専用です。|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>\<clientCredentials>構成での値の設定  

 資格情報の値は、要素の子要素としてエンドポイントの動作を使用して指定し [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) ます。 使用される要素は、クライアントの資格情報の種類によって異なります。 たとえば、次の例では、<を使用して x.509 証明書を設定する構成を示して [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) います。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
 構成でクライアント資格情報を設定するには、 [\<endpointBehaviors>](../configure-apps/file-schema/wcf/endpointbehaviors.md) 構成ファイルに要素を追加します。 さらに、 `behaviorConfiguration` 次の例に示すように、 [ \<endpoint> \<client> ](../configure-apps/file-schema/wcf/endpoint-of-client.md)追加された behavior 要素は、要素のの属性を使用してサービスのエンドポイントにリンクされている必要があります。 `behaviorConfiguration` 属性の値は、動作の `name` 属性の値と一致する必要があります。  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> クライアント資格情報の値の中には、アプリケーション構成ファイルを使用して設定できないものがあります (ユーザー名とパスワードや、Windows ユーザーとパスワードの値など)。 このような資格情報の値は、コードでのみ指定できます。  
  
 クライアント資格情報の設定の詳細については、「 [方法: クライアント資格情報の値を指定する](how-to-specify-client-credential-values.md)」を参照してください。  
  
> [!NOTE]
> 次の構成例に示すように、`ClientCredentialType` が `SecurityMode` に設定されている場合、`"TransportWithMessageCredential",` は無視されます。  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"
               establishSecurityContext="false"
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)
- [構成エディター ツール (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)
- [サービスのセキュリティ保護](securing-services.md)
- [WCF クライアントを使用したサービスへのアクセス](accessing-services-using-a-wcf-client.md)
- [方法: クライアントの資格情報の値を指定する](how-to-specify-client-credential-values.md)
- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [方法: クライアントの資格情報の種類を指定する](how-to-specify-the-client-credential-type.md)
