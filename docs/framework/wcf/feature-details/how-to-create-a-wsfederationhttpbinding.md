---
title: '方法: WSFederationHttpBinding を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: ccc28c46e8be0b835cf08d372ef85b8a66e989ef
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595441"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>方法: WSFederationHttpBinding を作成する

Windows Communication Foundation (WCF) では、 <xref:System.ServiceModel.WSFederationHttpBinding> クラス ( [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 構成) はフェデレーションサービスを公開するためのメカニズムを提供します。 これはクライアントに対して認証を要求するサービスであって、認証にはセキュリティ トークン サービスが発行するセキュリティ トークンが必要となります。 このトピックでは、必要な処理をコード中に埋め込む形、あるいは構成ファイルに必要な記述を加える形で、<xref:System.ServiceModel.WSFederationHttpBinding> の設定をする手順を説明します。 バインディングを作成すると、エンドポイントを設定してこのバインディングを使用できるようになります。

 基本的な手順の概略を以下に示します。

1. セキュリティ モードを選択します。 <xref:System.ServiceModel.WSFederationHttpBinding> には、メッセージ レベルでエンドツーエンドのセキュリティを提供する `Message` を指定できます。複数のホップや `TransportWithMessageCredential` にまたがる通信であってもこれは有効です。クライアントとサービスが HTTPS 上で直接接続できる場合に、特に性能を発揮します。

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding> には、セキュリティ モードとして `None` を指定することもできます。 このモードは安全性が低く、デバッグ目的での使用のみを目的としています。 サービスエンドポイントが、セキュリティモードがに設定されたを使用してデプロイされている場合 <xref:System.ServiceModel.WSFederationHttpBinding> `None` 、( [ServiceModel メタデータユーティリティツール (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)によって生成される) クライアントバインディングは、 <xref:System.ServiceModel.WSHttpBinding> セキュリティモードがののに `None` なります。

     `WSFederationHttpBinding` の場合、システムに組み込まれている他のバインディングとは違って、クライアント資格情報の種類を選択する必要はありません。 これは、常に、発行されたトークンを資格情報として使うからです。 WCF は、指定された発行者からトークンを取得し、そのトークンをサービスに提示してクライアントを認証します。

2. フェデレーション クライアントの場合、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> プロパティの値として、セキュリティ トークン サービスの URL を指定します。 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> としてバインディングを指定し、セキュリティ トークン サービスとの通信に使用します。

3. 任意。 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> プロパティの値として、トークンの種類の URI (Uniform Resource Identifier) を指定します。 フェデレーション サービスについては、提示されれば受理できるトークンの種類を指定します。 フェデレーション クライアントについては、セキュリティ トークン サービスに要求するトークンの種類を指定します。

     トークンの種類を指定しなければ、クライアント側ではその URI なしで WS-Trust のセキュリティ トークン要求 (RTS) を生成します。また、サービス側では、クライアントが既定で SAML (Security Assertions Markup Language) 1.1 のトークンを提示して認証するものと想定します。

     SAML 1.1 トークンの URI は `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` です。

4. 任意。 フェデレーション サービスの場合、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> プロパティの値として、セキュリティ トークン サービスのメタデータ URL を指定します。 メタデータ エンドポイントは、サービスがメタデータを公開するよう設定されている場合に、クライアントが適切なバインディング/エンドポイントのペアを選択するために必要です。 メタデータの公開の詳細については、「[メタデータの公開](publishing-metadata.md)」を参照してください。

 他に設定できるプロパティとしては、発行されたトークンの証明キーとして使用するキーの種類、クライアント/サーバー間で使用するアルゴリズム スイート、サービス資格情報をネゴシエートするか明示的に指定するか、トークンに入っていればそれに応じてサービス側で処理できるクレームの種類、クライアントがセキュリティ トークン サービスに送信する要求に追加しなければならない他の XML 要素などがあります。

> [!NOTE]
> `NegotiateServiceCredential` プロパティが意味をなすのは、`SecurityMode` の設定値が `Message` である場合に限ります。 `SecurityMode` の設定値が `TransportWithMessageCredential` であれば、`NegotiateServiceCredential` プロパティは無視されます。

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>必要な処理をコード中に埋め込む形で WSFederationHttpBinding を設定するには

1. <xref:System.ServiceModel.WSFederationHttpBinding> のインスタンスを作成します。

2. 必要に応じて、<xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.WSFederationHttpSecurityMode> または <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> に設定します。 以外のアルゴリズムスイート <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> が必要な場合は、 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> プロパティをから取得した値に設定し <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> ます。

3. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> プロパティに適切な値を設定します。

4. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A>プロパティをまたはに設定し <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` ます。`AsymmetricKey` 必要に応じて。

5. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> プロパティに適切な値を設定します。 値が設定されていない場合、WCF の既定値はに `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` なります。これは、SAML 1.1 トークンを示します。

6. クライアント側ではローカル発行者が指定されていなければ必須。サービス側では省略可能。 セキュリティ トークン サービスのアドレスと ID 情報が設定された <xref:System.ServiceModel.EndpointAddress> を作成し、この <xref:System.ServiceModel.EndpointAddress> インスタンスを <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> プロパティに代入します。

7. クライアント側ではローカル発行者が指定されていなければ必須。サービス側では不要。 のを作成し、その <xref:System.ServiceModel.Channels.Binding> `SecurityTokenService` <xref:System.ServiceModel.Channels.Binding> インスタンスをプロパティに割り当て <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> ます。

8. クライアント側では不要。サービス側では省略可能。 セキュリティ トークン サービスのメタデータ用の <xref:System.ServiceModel.EndpointAddress> インスタンスを作成し、`IssuerMetadataAddress` プロパティに代入します。

9. クライアント側、サービス側とも省略可能。 必要な数の <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> インスタンスを生成し、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> プロパティで返されたコレクションに追加します。

10. クライアント側、サービス側とも省略可能。 必要な数の <xref:System.Xml.XmlElement> インスタンスを生成し、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> プロパティで返されたコレクションに追加します。

## <a name="to-create-a-federated-endpoint-in-configuration"></a>構成ファイルに必要な記述を加える形でフェデレーション エンドポイントを作成するには

1. [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)アプリケーション構成ファイル内の要素の子として、を作成し [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) ます。

2. [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)の子として要素を作成 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) し、 `name` 属性に適切な値を設定します。

3. 要素 `<security>` の子として要素を作成 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) します。

4. 必要に応じて、`mode` 要素の `<security>` 属性値に `Message` または `TransportWithMessageCredential` を設定します。

5. `<message>` 要素の子要素として `<security>` 要素を作成します。

6. 任意。 `algorithmSuite` 要素の `<message>` 属性に適切な値を設定します。 既定値は、`Basic256` です。

7. 任意。 非対称証明キーが必要ならば、`issuedKeyType` 要素の `<message>` 属性を `AsymmetricKey` に設定します。 既定値は、`SymmetricKey` です。

8. 任意。 `issuedTokenType` 要素の `<message>` 属性を設定します。

9. クライアント側ではローカル発行者が指定されていなければ必須。サービス側では省略可能。 `<issuer>` 要素の子要素として `<message>` 要素を作成します。

10. `address` 要素に `<issuer>` 属性を設定し、セキュリティ トークン サービスがトークン要求を受け付けるアドレスを指定します。

11. 任意。 `<identity>` 子要素を追加し、セキュリティ トークン サービスの識別子を指定します。

12. 詳細については、「[サービス id と認証](service-identity-and-authentication.md)」を参照してください。

13. クライアント側ではローカル発行者が指定されていなければ必須。サービス側では不要。 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)Security Token Service との通信に使用できる要素をバインドセクションに作成します。 バインディングの作成の詳細については、「[方法: 構成でサービスバインディングを指定](../how-to-specify-a-service-binding-in-configuration.md)する」を参照してください。

14. `binding` 要素の `bindingConfiguration` 属性および `<issuer>` 属性に設定して、前の手順で作成したバインディングを指定します。

15. クライアント側では不要。サービス側では省略可能。 要素を `<issuerMetadata>` <> 要素の子として作成 `message` します。 次に、`address` 要素の `<issuerMetadata>` 属性に、セキュリティ トークン サービスがメタデータを公開するアドレスを指定します。 オプションで、`<identity>` 子要素を追加し、セキュリティ トークン サービスの識別子を指定します。

16. クライアント側、サービス側とも省略可能。 `<claimTypeRequirements>` 要素の子要素として `<message>` 要素を追加します。 要素 [\<add>](../../configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) に要素を追加 `<claimTypeRequirements>` し、属性を使用して要求の種類を指定することによって、サービスが依存する必須および省略可能な要求を指定し `claimType` ます。 さらに、`isOptional` 属性に、クレームが必須か省略可能かを設定します。

## <a name="example"></a>例

強制的に `WSFederationHttpBinding` を設定するコード例を以下に示します。

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>関連項目

- [フェデレーション](federation.md)
- [フェデレーション サンプル](../samples/federation-sample.md)
- [方法: WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
