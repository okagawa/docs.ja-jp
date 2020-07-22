---
title: <configuration> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921245"
---
# <a name="configuration-element"></a>\<configuration> 要素

共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。

**\<configuration>**

## <a name="syntax"></a>構文

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>属性

なし

## <a name="parent-element"></a>親要素

なし

## <a name="child-elements"></a>子要素

|     | Description |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | 構成レベルでのアセンブリ バインディング ポリシーを指定します。|
| [**\<startup>** 設定スキーマ](./startup/index.md) | スタートアップ設定スキーマのすべての要素。 |
| [**\<runtime>** 設定スキーマ](./runtime/index.md) | ランタイム設定スキーマ内のすべての要素。 |
| [**\<system.runtime.remoting>** 設定スキーマ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | リモート処理設定スキーマのすべての要素。 |
| [**\<system.Net>** 設定スキーマ](./network/index.md) | ネットワーク設定スキーマのすべての要素。 |
| [**\<cryptographySettings>** 設定スキーマ](./cryptography/index.md) | 暗号化設定スキーマのすべての要素。 |
| [**\<configuration>** セクションスキーマ](configuration-sections-schema.md) | 構成セクション設定スキーマ内のすべての要素。 |
| [トレースおよびデバッグ設定のスキーマ](./trace-debug/index.md) | トレースおよびデバッグ設定スキーマのすべての要素。 |
| [ASP.NET 構成設定スキーマ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | ASP.NET 構成スキーマのすべての要素。 ASP.NET Web サイトおよびアプリケーションを構成するための要素が含まれています。 *Web.config ファイルで*使用されます。 |
| [**\<webServices>** 設定スキーマ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Web サービス設定スキーマ内のすべての要素。 |
| [Web 設定スキーマ](./web/index.md) | IIS などのホスト アプリケーションと ASP.NET の連携を構成する要素も含め、Web 設定スキーマのすべての要素。 *Aspnet*ファイルで使用されます。 |

## <a name="remarks"></a>解説

各構成ファイルには、要素が1つだけ含まれている必要があり **\<configuration>** ます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
