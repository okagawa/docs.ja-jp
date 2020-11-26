---
title: '方法: カスタム証明書検証を使用するサービスを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 31918ca2d96b63911130d22476a6e5a6d48999ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249242"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>方法: カスタム証明書検証を使用するサービスを作成する

このトピックでは、カスタム証明書検証を実装する方法、クライアントまたはサービスの資格情報の設定により、既定の証明書検証機能を、カスタム証明書検証で置き換える方法について解説します。  
  
 X.509 証明書を使用してクライアントまたはサービスを認証する場合、Windows Communication Foundation (WCF) では、既定で Windows 証明書ストアと Crypto API を使用して証明書を検証し、証明書が信頼されていることを確認します。 ただし、組み込みの検証機能では不十分で、処理内容を変更する必要がある場合もあります。 WCF では、ユーザーがカスタム証明書検証機能を追加できるようにすることで、検証ロジックを簡単に変更できます。 カスタム証明書検証コントロールが指定されている場合、WCF は組み込みの証明書検証ロジックを使用しませんが、代わりにカスタム検証機能に依存します。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-create-a-custom-certificate-validator"></a>カスタムの証明書検証機能を作成するには  
  
1. <xref:System.IdentityModel.Selectors.X509CertificateValidator> から派生する新しいクラスを定義します。  
  
2. 抽象メソッドである <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> を実装します。 検証対象の証明書が、引数としてこのメソッドに渡されます。 検証処理の結果、証明書が無効であると判断されると、このメソッドは、<xref:System.IdentityModel.Tokens.SecurityTokenValidationException> という例外をスローします。 有効であればそのまま呼び出し元に制御を返します。  
  
    > [!NOTE]
    > クライアントに認証エラーを返すには、<xref:System.ServiceModel.FaultException> メソッドで <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> をスローします。  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>サービス構成でカスタム検証処理を指定するには  
  
1. 要素 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) とを [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 要素に追加し [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) ます。  
  
2. を追加 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) し、 `name` 属性を適切な値に設定します。  
  
3. を [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 要素に追加し `<behavior>` ます。  
  
4. `<clientCertificate>` 要素を `<serviceCredentials>` 要素に追加します。  
  
5. [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)要素にを追加 `<clientCertificate>` します。  
  
6. `customCertificateValidatorType` 属性に検証処理の型を設定します。 この属性に型の名前空間と名前を設定する例を以下に示します。  
  
7. `certificateValidationMode` 属性を `Custom` に設定します。  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>クライアント側の設定でカスタム証明書検証を指定するには  
  
1. 要素 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) とを [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 要素に追加し [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) ます。  
  
2. 要素を追加 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) します。  
  
3. `<behavior>` 要素を追加し、`name` 属性に適切な値を設定します。  
  
4. 要素を追加 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) します。  
  
5. を追加 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) します。  
  
6. 次の [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) 例に示すように、を追加します。  
  
7. `customCertificateValidatorType` 属性に検証処理の型を設定します。  
  
8. `certificateValidationMode` 属性を `Custom` に設定します。 この属性に型の名前空間と名前を設定する例を以下に示します。  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>サービス側のコードでカスタム証明書検証を指定するには  
  
1. <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> プロパティの値としてカスタム証明書検証を指定します。 サービスの資格情報には、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A> プロパティを使用してアクセスできます。  
  
2. <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> プロパティを <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>に設定します。  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>クライアント側のコードでカスタム証明書検証を指定するには  
  
1. カスタム証明書検証を、<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> プロパティを使って指定します。 クライアントの資格情報には、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A> プロパティを使用してアクセスできます。 ( [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) によって生成されるクライアントクラスは、常にクラスから派生し <xref:System.ServiceModel.ClientBase%601> ます)。  
  
2. <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> プロパティを <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>に設定します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  

 カスタム証明書検証を実装し、サービス側で使用する例を以下に示します。  
  
### <a name="code"></a>コード  

 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
