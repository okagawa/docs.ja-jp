---
description: '詳細情報: <defaultFtpCachePolicy> 要素 (ネットワーク設定)'
title: <defaultFtpCachePolicy> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 77150ce0980e96dd949df4b5ad7e4557ed1b991a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740367"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a>\<defaultFtpCachePolicy> 要素 (ネットワーク設定)

FTP キャッシュがアクティブかどうか、および既定のキャッシュポリシーについて説明します。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a>構文  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`policyLevel`|FTP キャッシュポリシーを指定します。 既定値は `Default` です。|  
  
## <a name="policylevel-attribute"></a>policyLevel 属性  
  
|値|説明|  
|-----------|-----------------|  
|`Default`|リソースが最新で、コンテンツの長さが正確で、有効期限、変更、およびコンテンツの長さの属性が存在する場合、キャッシュされたリソースを返します。|  
|`BypassCache`|サーバーからリソースを返します。|  
|`CacheOnly`|コンテンツの長さが存在し、エントリのサイズと一致する場合、キャッシュされたリソースを返します。|  
|`CacheIfAvailable`|コンテンツの長さが指定され、エントリのサイズと一致する場合に、キャッシュされたリソースを返します。それ以外の場合は、リソースがサーバーからダウンロードされ、呼び出し元に返されます。|  
|`Revalidate`|キャッシュされたリソースのタイムスタンプがサーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースを返します。それ以外の場合は、リソースがサーバーからダウンロードされ、キャッシュに格納されて、呼び出し元に返されます。|  
|`Reload`|サーバーからリソースをダウンロードし、キャッシュに格納して、リソースを呼び出し元に返します。|  
|`NoCacheNoStore`|キャッシュされたリソースが存在する場合は、削除されます。 リソースはサーバーからダウンロードされ、呼び出し元に返されます。|  
|`Revalidate`|タイムスタンプがサーバーのリソースのタイムスタンプと同じ場合は、キャッシュされたリソースのコピーを使用して要求に応じます。それ以外の場合は、リソースがサーバーからダウンロードされ、呼び出し元に提示され、キャッシュに格納されます。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Requestcaching>](requestcaching-element-network-settings.md)|ネットワーク要求のキャッシュメカニズムを制御します。|  
  
## <a name="remarks"></a>解説  
  
## <a name="example"></a>例  

 次の例は、の FTP キャッシュポリシーを指定する方法を示して `NoCacheNoStore` います。  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [ネットワーク設定スキーマ](index.md)
