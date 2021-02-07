---
description: '詳細については、次のページを参照してください: <system.web> 要素 (Web 設定)'
title: <system.web> 要素 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: 2adcd3eba1eb6d67bcb4dc82243cd70d31d64fe9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681904"
---
# <a name="systemweb-element-web-settings"></a>\<system.web> 要素 (Web 設定)

ASP.NET ホスティングレイヤーがプロセス全体の動作をどのように管理するかについて説明します。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|aspnet.config ファイル内の IIS アプリケーションプールの構成設定を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素を指定します。|  
  
## <a name="remarks"></a>解説  

`system.web`要素とその子 `applicationPool` 要素が .NET FRAMEWORK 3.5 SP1 の .NET Framework に追加されました。 IIS 7.0 以降のバージョンを統合モードで実行すると、この要素の組み合わせによって、ASP.NET がどのようにスレッドを管理し、ASP.NET が IIS アプリケーションプールでホストされている場合の要求をキューに配置するかを構成できます。 IIS 7.0 以降のバージョンをクラシックモードまたは ISAPI モードで実行した場合、これらの設定は無視されます。  
  
## <a name="example"></a>例  

次の例では、IIS アプリケーションプールで ASP.NET がホストされている場合に、aspnet.config ファイルに ASP.NET プロセス全体の動作を構成する方法を示します。 この例では、IIS が統合モードで実行されており、アプリケーションが .NET Framework 3.5 SP1 以降のバージョンを使用していることを前提としています。 この動作は、.NET Framework 3.5 SP1 より前のバージョンの .NET Framework では発生しません。 この例の値は既定値です。  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|名前空間||  
|スキーマ名||  
|検証ファイル||  
|空にすることができます||  
  
## <a name="see-also"></a>関連項目

- [\<applicationPool> 要素 (Web 設定)](applicationpool-element-web-settings.md)
