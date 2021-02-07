---
description: '詳細情報: <clear> bypasslist の要素 (ネットワーク設定)'
title: bypasslist の <clear> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 4ddb66c837c55391a19826c44c6df7a3e88c8e0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729901"
---
# <a name="clear-element-for-bypasslist-network-settings"></a>bypasslist の \<clear> 要素 (ネットワーク設定)

プロキシバイパスリストをクリアします。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>構文  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

 なし。  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|プロキシを使用しないアドレスを記述する一連の正規表現を提供します。|  
  
## <a name="remarks"></a>解説  

 要素は、 `clear` バイパスリストからすべてのエントリを削除します。  
  
## <a name="configuration-files"></a>構成ファイル  

 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  

 次の例では、バイパスリストをクリアし、2つのアドレスをバイパスリストに追加します。 最初のは、contoso.com ドメイン内のすべてのサーバーのプロキシをバイパスします。2つ目は、IP アドレスが192.168 で始まるすべてのサーバーのプロキシをバイパスします。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](index.md)
