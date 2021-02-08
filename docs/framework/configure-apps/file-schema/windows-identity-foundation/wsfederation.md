---
description: '詳細情報: <wsFederation>'
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: f28c140816dc6de6d618772d5213d6ab094b78c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802126"
---
# \<wsFederation>

<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfam) の構成を提供します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederation>**  
  
## <a name="syntax"></a>構文  
  
```xml
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
                  freshness=xs:decimal  
                  homerealm=xs:string (URI)  
                  issuer=xs:string (URI)  
                  persistentCookiesOnPassiveRedirects=xs:boolean  
                  passiveRedirectEnabled=xs:boolean  
                  policy=xs:string (URI)  
                  realm=xs:string (URI)  
                  reply=xs:string (URI)  
                  request=xs:string (URI)  
                  requestPtr=xs:string (URI)  
                  requireHttps=xs:boolean  
                  resource=xs:string (URI)  
                  signInQueryString=xs:string  
                  signOutQueryString=xs:string  
                  signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|authenticationType|認証の種類を指定する URI。 WS-Federation サインイン要求の wauth パラメーターを設定します。 任意。 既定値は空の文字列です。これは、wauth パラメーターが要求に含まれないことを指定します。|  
|鮮度|分単位の、希望する認証要求の最大期間。 WS-Federation サインインの要求 wfresh パラメーターを設定します。 省略可能。 既定値は 0 です。 任意。 **警告:**  .NET Framework 4.5 の次のリリースでは、 `freshness` 属性は型になり、 `xs:string` その既定値はになり `null` ます。|  
|homeRealm|認証に使用する id プロバイダー (IdP) のホーム領域。 WS-Federation サインインの要求 whr パラメーターを設定します。 省略可能。 既定値は空の文字列です。これは、whr パラメーターが要求に含まれないことを指定します。|  
|発行者|目的のトークン発行者の URI。 WS-Federation サインイン要求とサインアウト要求のベース URL を設定します。|  
|persistentCookiesOnPassiveRedirects|認証時に永続的な cookie を発行するかどうかを指定します。 任意。 既定値は "false" です。 cookie は発行されません。|  
|無効化 Veredirectenabled|承認されていない要求を STS に自動的にリダイレクトするために WSFAM が有効かどうかを指定します。 任意。 既定値は "true" で、承認されていない要求は自動的にリダイレクトされます。|  
|policy|サインイン要求で使用する関連ポリシーの場所を指定する URL。 既定値は空の文字列です。 WS-Federation サインインの要求 wp パラメーターを設定します。 省略可能。 既定値は空の文字列です。これは、wp パラメーターが要求に含まれないことを指定します。|  
|realm|要求している領域の URI。 (STS (Security Token Service) に証明書利用者 (RP) を識別する URI。要求の wtrealm WS-Federation サインイン要求パラメーターを設定します。 必須。|  
|reply|証明書利用者 (RP) アプリケーションがセキュリティ トークン サービス (STS) から応答を受信することを希望しているアドレスを識別する URL。 WS-Federation サインイン要求の wreply パラメーターを設定します。 任意。 既定値は空の文字列です。これは、wreply パラメーターが要求に含まれないことを指定します。|  
|request|トークン発行要求。 WS-Federation サインインの要求 wreq パラメーターを設定します。 省略可能。 既定値は空の文字列です。これは、wreq パラメーターが要求に含まれないことを指定します。 要求に wreq または wreqptr パラメーターを含めないことは、発行するトークンの種類を STS が認識していることを意味します。|  
|requestPtr|トークン発行要求の場所を指定する URL 要求の wreqptr パラメーターを設定します。 任意。 既定値は空の文字列です。これは、wreqptr パラメーターが要求に含まれないことを指定します。 要求に wreq または wreqptr パラメーターを含めないことは、発行するトークンの種類を STS が認識していることを意味します。|  
|requireHttps|Security Token Service (STS) との通信で HTTPS プロトコルを使用する必要があるかどうかを指定します。 任意。 既定値は "true"、HTTPS を使用する必要があります。|  
|resource|セキュリティ トークン サービスに対してアクセスされるリソース、証明書利用者 (RP) を識別する URI。 任意。 WS-Federation サインイン要求の wres パラメーターを設定します。 任意。 既定値は空の文字列です。これは、wres パラメーターが要求に含まれないことを指定します。 **注:**  wres は従来のパラメーターです。 `realm`代わりに、wtrealm パラメーターを使用する属性を指定してください。|  
|signInQueryString|WS-Federation サインイン要求 URL でアプリケーション定義のクエリパラメーターを指定する機能拡張ポイントを提供します。 任意。 既定値は空の文字列です。これは、要求に追加のパラメーターを含める必要がないことを指定します。 パラメーターは、次の形式を使用してクエリ文字列フラグメントとして指定され `"param1=value1&param2=value2&param3=value3"` ます。 **注:**  構成ファイルでは、クエリ文字列の ' & ' 文字をエンティティ参照を使用して指定する必要があり `&` ます。|  
|signOutQueryString|WS-Federation サインイン要求 URL でアプリケーション定義のクエリパラメーターを指定する機能拡張ポイントを提供します。 任意。 既定値は空の文字列です。これは、要求に追加のパラメーターを含める必要がないことを指定します。 パラメーターは、次の形式を使用してクエリ文字列フラグメントとして指定され `"param1=value1&param2=value2&param3=value3"` ます。 **注:**  構成ファイルでは、クエリ文字列の ' & ' 文字をエンティティ参照を使用して指定する必要があり `&` ます。|  
|signOutReply|WS-Federation プロトコルを使用したパッシブサインアウト中に、クライアントが Security Token Service (STS) によってリダイレクトされる URL を指定します。 WS-Federation サインアウト要求の wreply パラメーターを設定します。 任意。 既定値は空の文字列です。これは、要求に追加のパラメーターを含める必要がないことを指定します。|  
  
### <a name="child-elements"></a>子要素  

 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfam) と (SAM) を構成する設定が含まれてい <xref:System.IdentityModel.Services.SessionAuthenticationModule> ます。|  
  
## <a name="remarks"></a>解説  

 要素を使用して、 `<wsFederation>` WSFAM の既定の WS-Federation パラメーター設定と既定の動作を構成できます。 クラスによって公開される同等のプロパティを設定する要素で定義されているパラメーター設定を WS-Federation し `<wsFederation>` <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> ます。 これらのプロパティは、WSFAM によって発行されたすべての要求で同じままです。 WSFAM によって公開されるイベントのイベントハンドラーを追加することで、要求の処理中に WS-Federation パラメーターを動的に変更できます。たとえば、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> イベントです。 詳細については、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> クラスのドキュメントをご覧ください。  
  
 `<wsFederation>`要素は、クラスによって表され <xref:System.IdentityModel.Services.Configuration.WSFederationElement> ます。 構成オブジェクト自体は、クラスによって表され <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> ます。 プロパティを <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> 通じてアクセスされるオブジェクトに対して1つのインスタンスが設定され、 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> wsfam の構成が提供されます。  
  
## <a name="example"></a>例  

 次の XML は、 `<wsFederation>` WSFAM の設定を指定する要素を示しています。  
  
> [!WARNING]
> この例では、WSFAM は HTTPS を使用する必要はありません。 これは、 `requireHttps` 要素の属性 `<wsFederation>` が設定されているためです `false` 。 ほとんどの運用環境では、セキュリティ上のリスクが生じる可能性があるため、この設定は推奨されません。  
  
```xml
<wsFederation passiveRedirectEnabled="true"
              issuer="http://localhost:15839/wsFederationSTS/Issue"
              realm="http://localhost:50969/"
              reply="http://localhost:50969/"
              requireHttps="false"
              signOutReply="http://localhost:50969/SignedOutPage.html"
              signOutQueryString="Param1=value2&Param2=value2"
              persistentCookiesOnPassiveRedirects="true" />
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
