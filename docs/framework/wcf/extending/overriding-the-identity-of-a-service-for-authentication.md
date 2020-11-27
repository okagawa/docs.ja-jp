---
title: 認証のためのサービスの ID のオーバーライド
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: a02e5a2f69ad1819e6ab98b0454dd64599382cd0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262778"
---
# <a name="override-the-identity-of-a-service-for-authentication"></a>認証のためにサービスの id をオーバーライドする

クライアント資格情報の種類を選択すると、サービス メタデータで公開される ID の種類が指定されるため、通常、サービスで ID を設定する必要はありません。 たとえば、次の構成コードでは、 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 要素を使用して、属性を Windows に設定して `clientCredentialType` います。  

 次の Web サービス記述言語 (WSDL) コードは、定義済みのエンドポイントの ID を示しています。 この例では、サービスが特定のユーザーアカウント () で自己ホスト型サービスとして実行され username@contoso.com ているため、ユーザープリンシパル名 (UPN) id にアカウント名が含まれています。 UPN は、Windows ドメインのユーザーサインイン名とも呼ばれます。  

 Id 設定を示すサンプルアプリケーションについては、「 [サービス id のサンプル](../samples/service-identity-sample.md)」を参照してください。 サービス id の詳細については、「 [サービス id と認証](../feature-details/service-identity-and-authentication.md)」を参照してください。  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos 認証と ID  

 既定では、サービスが Windows 資格情報を使用するように構成されている場合、 [\<identity>](../../configure-apps/file-schema/wcf/identity.md) [\<userPrincipalName>](../../configure-apps/file-schema/wcf/userprincipalname.md) 要素または要素を含む要素 [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) が WSDL で生成されます。 サービスが、、またはのいずれかのアカウントで実行されている場合 `LocalSystem` `LocalService` `NetworkService` 、既定では、サービスプリンシパル名 (spn) がという形式で生成され `host/` \<*hostname*> ます。これらのアカウントは、コンピューターの SPN データにアクセスできるためです。 サービスが別のアカウントで実行されている場合、Windows Communication Foundation (WCF) は、domainName という形式の UPN を生成し \<*username*> @< *domainName* `>` ます。 これらが生成されるのは、Kerberos 認証では、サービスを認証するために UPN または SPN をクライアントに提供する必要があるからです。  
  
 [Setspn](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731241(v=ws.10))ツールを使用して、ドメイン内のサービスアカウントに追加の SPN を登録することもできます。 登録した SPN は、そのサービスの ID として使用できます。 ツールの詳細については、「 [Setspn の概要](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))」を参照してください。  
  
> [!NOTE]
> ネゴシエーションを行わずに Windows 資格情報を使用するには、サービスのユーザー アカウントが Active Directory ドメインに登録された SPN にアクセスできる必要があります。 これは、次の方法で行うことができます。  
  
- サービスを実行するには、NetworkService アカウントまたは LocalSystem アカウントを使用します。 これらのアカウントは、コンピューターが Active Directory ドメインに参加したときに確立されたコンピューターの SPN にアクセスできるため、WCF はサービスのメタデータ (WSDL) でサービスのエンドポイント内の適切な SPN 要素を自動的に生成します。  
  
- 任意の Active Directory ドメイン アカウントを使用してサービスを実行します。 この場合、そのドメイン アカウント用の SPN を確立します。これには、Setspn.exe ユーティリティ ツールを使用できます。 サービスのアカウントの SPN を作成したら、その SPN をメタデータ (WSDL) を通じてサービスのクライアントに発行するように WCF を構成します。 これを行うには、アプリケーション構成ファイルまたはコードを使用して、公開されるエンドポイントのエンドポイント ID を設定します。  
  
 Spn、Kerberos プロトコル、および Active Directory の詳細については、「 [Windows 用の Kerberos テクニカル補完](/previous-versions/msp-n-p/ff649429(v=pandp.10))」を参照してください。  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>SPN または UPN が空の文字列の場合  

 空の文字列の SPN または UPN を設定した場合は、使用しているセキュリティ レベルと認証モードに応じて、次のようになります。  
  
- トランスポート レベルのセキュリティを使用している場合は、NTLM (NT LanMan) 認証が選択されます。  
  
- メッセージ レベルのセキュリティを使用している場合は、認証モードによっては認証に失敗する可能性があります。  
  
- モードを使用していて、属性がに設定されている場合 `spnego` `AllowNtlm` `false` 、認証は失敗します。  
  
- モードを使用していて、属性がに設定されている場合 `spnego` `AllowNtlm` `true` 、UPN が空の場合、認証は失敗しますが、SPN が空の場合は成功します。  
  
- Kerberos ダイレクト ("ワンショット" とも呼ばれます) を使用している場合は、認証に失敗します。  
  
### <a name="use-the-identity-element-in-configuration"></a>\<identity>構成で要素を使用する  

 前に示したバインディングでクライアント資格情報の種類を変更した場合、生成された WSDL には、 `Certificate` 次のコードに示すように、id 値の Base64 でシリアル化された x.509 証明書が含まれます。 これは、Windows 以外のすべてのクライアント資格情報の種類の既定値です。  

 既定のサービス id の値を変更することも、id の種類を変更することもできます。そのためには、 `identity` 構成の <> 要素を使用するか、コードで id を設定します。 値 `contoso.com` を使用してドメイン ネーム システム (DNS) ID を設定する構成コードを次に示します。  

### <a name="set-identity-programmatically"></a>プログラムによる Id の設定  

 WCF によって自動的に決定されるため、サービスで id を明示的に指定する必要はありません。 ただし、WCF では、必要に応じてエンドポイントの id を指定できます。 特定の DNS ID を持つ新しいサービス エンドポイントを追加するコードを次に示します。  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [方法: カスタム クライアント ID 検証機能を作成する](how-to-create-a-custom-client-identity-verifier.md)
- [サービス ID と認証](../feature-details/service-identity-and-authentication.md)
