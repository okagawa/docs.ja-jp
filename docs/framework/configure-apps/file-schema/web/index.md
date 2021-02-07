---
description: '詳細情報: Web 設定スキーマ'
title: Web 設定スキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
ms.openlocfilehash: 262a53ae062788143cbacdc1012085186f4c9652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681917"
---
# <a name="web-settings-schema"></a>Web 設定スキーマ

Web 設定は、CPU と、ASP.NET ホスト層によって管理されているプロセス全体の動作に適用される CPU および ASP.NET 設定の実行レベルを指定します。 これらの設定は、ASP.NET アプリケーションの Web.config ファイルで指定されているアプリケーション ドメインの種類の設定とは異なります。  
  
Web 設定は、.NET Framework のバージョンのインストール フォルダーに配置された Aspnet.config ファイルに格納されます。 たとえば、.NET Framework 2.0 の Aspnet.config ファイルは次のフォルダーにあります。  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
Web 設定は、machine.config ファイル、ルート、Web.config ファイル、アプリケーション レベルの Web.config ファイルなどの他の構成ファイルでは使用されません。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|要素|説明|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|ASP.NET ホスト層が使用する情報が含まれています。|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|CPU と、ASP.NET ホスト層によって管理されているプロセス全体の動作に適用される CPU および ASP.NET 設定の実行レベルを指定します。|  
  
## <a name="see-also"></a>関連項目

- [構成ファイル スキーマ](../index.md)
