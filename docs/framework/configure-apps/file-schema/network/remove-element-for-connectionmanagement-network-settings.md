---
description: '詳細情報: <remove> connectionManagement の要素 (ネットワーク設定)'
title: connectionManagement の <remove> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 98916846fb5de93ee93a7e25530e983cbd3719ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740250"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a>connectionManagement の \<remove> 要素 (ネットワーク設定)

接続管理リストから IP アドレスまたは DNS 名を削除します。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>構文  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`address`|IP アドレスまたは DNS 名。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|ネットワーク ホストへの接続の最大数を指定します。|  
  
## <a name="remarks"></a>解説  

 要素は、 `remove` 指定されたサーバーの接続管理リストのエントリを削除します。  
  
 属性の値は、 `address` 有効な IP アドレスまたはホスト名である必要があります。  
  
## <a name="configuration-files"></a>構成ファイル  

 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  

 次の例では、サーバーに対する接続管理の一覧のエントリをすべて削除し、 `www.adventure-works.com` サーバーへの接続を4つ、 `www.contoso.com` 他のすべてのサーバーへの接続を2つ使用するようにアプリケーションを構成します。  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [ネットワーク設定スキーマ](index.md)
