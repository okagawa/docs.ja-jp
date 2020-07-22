---
title: <connectionManagement> 要素 (ネットワーク設定)
description: <connectionManagement>ネットワーク設定要素は、.NET Framework 内のネットワークホストへの接続の最大数を指定します。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 4ceec06fb0e21bfae67038efe0ce758d3d5b708f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504616"
---
# <a name="connectionmanagement-element-network-settings"></a>\<connectionManagement> 要素 (ネットワーク設定)
ネットワーク ホストへの接続の最大数を指定します。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a>構文  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[add](add-element-for-connectionmanagement-network-settings.md)|IP アドレスまたは DNS 名を接続管理リストに追加します。|  
|[オフ](clear-element-for-connectionmanagement-network-settings.md)|接続管理の一覧をクリアします。|  
|[remove](remove-element-for-connectionmanagement-network-settings.md)|接続管理リストから IP アドレスまたは DNS 名を削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## <a name="remarks"></a>解説  
 要素は、 `connectionManagement` サーバーまたはサーバーのグループへの接続の最大数を定義します。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、サーバーへの4つの接続 `www.contoso.com` と、他のすべてのサーバーへの2つの接続を使用するようにアプリケーションを構成します。  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [ネットワーク設定スキーマ](index.md)
