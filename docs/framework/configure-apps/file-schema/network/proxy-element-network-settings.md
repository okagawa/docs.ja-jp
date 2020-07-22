---
title: <proxy> 要素 (ネットワーク設定)
description: <proxy>ネットワーク設定要素は、.NET Framework のプロキシサーバーオプションを定義します。 この記事には例が含まれています。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 8ae30b8c29dcf3aaa183ff295c7ee8592322797f
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141782"
---
# <a name="proxy-element-network-settings"></a>\<proxy> 要素 (ネットワーク設定)
プロキシ サーバーを定義します。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a>構文  
  
```xml  
<proxy
  autoDetect="True|False|Unspecified"
  bypassonlocal="True|False|Unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="True|False|Unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`autoDetect`|プロキシを自動的に検出するかどうかを指定します。 既定値は `Unspecified` です。|  
|`bypassonlocal`|ローカル リソースの場合に、プロキシがバイパスされるかどうかを指定します。 ローカルリソースには、ローカルサーバー ( `http://localhost` 、 `http://loopback` 、または `http://127.0.0.1` ) と、ピリオドなしの URI () が含ま `http://webserver` れます。 既定値は `Unspecified` です。|  
|`proxyaddress`|使用するプロキシ URI を指定します。|  
|`scriptLocation`|構成スクリプトの場所を指定します。 この属性には属性を使用しない `bypassonlocal` でください。 |  
|`usesystemdefault`|Internet Explorer のプロキシ設定を使用するかどうかを指定します。 に設定する `True` と、それ以降の属性は Internet Explorer のプロキシ設定よりも優先されます。 既定値は `Unspecified` です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。|  
  
## <a name="text-value"></a>テキスト値  
  
## <a name="remarks"></a>注釈  
 要素は、 `proxy` アプリケーションのプロキシサーバーを定義します。 この要素が構成ファイルにない場合、.NET Framework は Internet Explorer のプロキシ設定を使用します。  
  
 属性の値は、整形 `proxyaddress` 式の Uniform Resource Indicator (URI) である必要があります。  
  
 属性は、 `scriptLocation` プロキシ構成スクリプトの自動検出を参照します。 <xref:System.Net.WebProxy>Internet Explorer で [**自動構成スクリプトを使用する**] オプションが選択されている場合、クラスは、(通常は wpad.dat という名前の) 構成スクリプトの検索を試みます。 が任意の値に設定されている場合 `bypassonlocal` 、 `scriptLocation` は無視されます。
  
 `usesystemdefault`バージョン2.0 に移行する .NET Framework バージョン1.1 アプリケーションの場合は、属性を使用します。  
  
 `proxyaddress`属性が無効な既定のプロキシを指定している場合は、例外がスローされます。 例外の <xref:System.Exception.InnerException%2A> プロパティに、このエラーの根本原因に関する詳細情報が含まれています。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、Internet Explorer プロキシの既定値を使用して、プロキシアドレスを指定し、ローカルアクセスのためにプロキシをバイパスします。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](index.md)
