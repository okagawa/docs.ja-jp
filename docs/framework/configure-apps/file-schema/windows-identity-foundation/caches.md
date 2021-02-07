---
description: '詳細情報: <caches>'
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: ebc2fa66ab8b657f7cc3741668c9f27fc60510b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681839"
---
# \<caches>

セッショントークンとトークンリプレイ検出に使用されるキャッシュを登録します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|セッショントークンのキャッシュをサービスまたはセキュリティトークンハンドラーコレクションに登録します。|  
|[\<tokenReplayCache>](tokenreplaycache.md)|トークン再生キャッシュをサービスまたはセキュリティトークンハンドラーコレクションに登録します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|サービスレベルの id 設定を指定します。|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|セキュリティトークンハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>解説  

 要素は `<caches>` 、要素の下のサービスレベルで指定することも、 `<identityConfiguration>` 要素の下のセキュリティトークンハンドラーコレクションレベルで指定することもでき `<securityTokenHandlerConfiguration>` ます。 トークンハンドラーコレクションの設定は、サービスで指定された設定よりも優先されます。  
  
 `<caches>`要素は、クラスによって表され <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> ます。 構成されたキャッシュは、クラスによって表され <xref:System.IdentityModel.Configuration.IdentityModelCaches> ます。  
  
## <a name="example"></a>例  

 次の XML は、セッションセキュリティトークン () を保持するためのカスタムキャッシュの構成を示して <xref:System.IdentityModel.Tokens.SessionSecurityToken> います。 この構成は、サンプルから取得され `ClaimsAwareWebFarm` ます。  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
