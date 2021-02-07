---
description: '詳細情報: <issuerTokenResolver>'
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 535b6f098e168a198eb0949d6baba6659e5140db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664094"
---
# \<issuerTokenResolver>

トークンハンドラーコレクションのハンドラーによって使用される発行者トークンリゾルバーを登録します。 発行者トークンリゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|type|発行者トークンリゾルバーの種類を指定します。 は、クラス <xref:System.IdentityModel.Tokens.IssuerTokenResolver> またはクラスから派生した型のいずれかである必要があり <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ます。 必須。|  
  
### <a name="child-elements"></a>子要素  

 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|セキュリティトークンハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>解説  

 発行者トークンリゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。 署名の確認に使用される暗号化マテリアルを取得するために使用されます。 属性を指定する必要があり `type` ます。 指定できる型は、 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> またはクラスから派生したカスタム型のいずれか <xref:System.IdentityModel.Tokens.IssuerTokenResolver> です。  
  
 一部のトークンハンドラーでは、構成で発行者トークンリゾルバーの設定を指定できます。 個々のトークンハンドラーの設定は、セキュリティトークンハンドラーコレクションで指定された設定よりも優先されます。  
  
> [!NOTE]
> 要素 `<issuerTokenResolver>` の子要素としての指定 [\<identityConfiguration>](identityconfiguration.md) は非推奨とされましたが、旧バージョンとの互換性のために引き続きサポートされています。 要素の設定は、要素の設定 `<securityTokenHandlerConfiguration>` よりも優先さ `<identityConfiguration>` れます。  
  
## <a name="example"></a>例  

 次の XML は、から派生したカスタムクラスに基づく発行者トークンリゾルバーの構成を示して <xref:System.IdentityModel.Tokens.IssuerTokenResolver> います。 トークンリゾルバーは、 `<AddAudienceKeyPair>` クラスに対して定義されているカスタム構成要素 () から初期化される、ユーザーとキーのペアのディクショナリを保持します。 クラスは、メソッドをオーバーライドして <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> この要素を処理します。 オーバーライドを次の例に示します。ただし、簡潔にするために呼び出すメソッドは表示されません。 完全な例については、「」のサンプルを参照してください `CustomToken` 。  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>例
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
