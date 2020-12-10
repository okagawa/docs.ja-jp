---
title: <configuration> の <appSettings> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: 66260d15768781b7fa3d9397b8e8a7d9ad68ab95
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009795"
---
# <a name="appsettings-element-for-configuration"></a>\<configuration> の \<appSettings> 要素

カスタムアプリケーション設定が含まれます。 これは、.NET Framework によって提供される定義済みの構成セクションです。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<appSettings>**

## <a name="syntax"></a>構文

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **file**  | 省略可能な属性です。<br><br>カスタムアプリケーション構成設定を含む外部ファイルへの相対パスを指定します。 指定したファイルには、、、およびの各要素で指定したものと同じ種類の設定が含まれて **\<add>** **\<remove>** おり、これらの **\<clear>** 要素と同じキー/値ペアの形式を使用します。<br><br>指定されたパスは、メイン構成ファイルに対する相対パスです。 Windows フォームアプリケーションの場合、これはアプリケーション構成ファイルの場所ではなく、バイナリフォルダー ( */bin/debug* など) です。 Web フォームアプリケーションの場合、パスはアプリケーションルートに対して相対的で、 *web.config* ファイルが配置されます。<br><br>指定されたファイルが見つからない場合、ランタイムは属性を無視します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<configuration>** 要素](../configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-elements"></a>子要素

|     | 説明 |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | カスタムアプリケーション設定を追加します。 |
| [**\<clear>**](clear-element-for-appsettings.md) | 以前に定義したアプリケーション設定をすべてクリアします。 |
| [**\<remove>**](remove-element-for-appsettings.md) | 以前に定義したアプリケーション設定を削除します。 |

## <a name="remarks"></a>注釈

要素には、 **\<appSettings>** データベース接続文字列、ファイルパス、XML Web サービス url などのカスタムアプリケーション構成情報、またはアプリケーションのその他のカスタム構成情報が格納されます。 要素で指定されたキーと値のペア **\<appSettings>** は、クラスを使用してコードでアクセスされ <xref:System.Configuration.ConfigurationSettings> ます。

**ファイル** 属性は、 **\<appSettings>** *Web.config* とアプリケーション構成ファイルの要素で使用できます。 この属性は、追加設定を提供するか、要素で指定された設定をオーバーライドする構成ファイルを指定し **\<appSettings>** ます。 **ファイル** 属性は、アプリケーション構成ファイルで指定されたプロジェクト設定をユーザーがオーバーライドする必要がある場合など、ソース管理チームの開発シナリオで使用できます。

**File** 属性で指定される構成ファイルは、ではなく、のルートノードである必要があり **\<appSettings>** **\<configuration>** ます。

## <a name="example"></a>例

次の例は、カスタム アプリケーション設定を定義する外部アプリケーション設定ファイル (*custom.config*) を示しています。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

次の例は、外部設定ファイルで設定を使用して、独自のアプリケーション設定を設定するアプリケーション構成ファイルを示しています。

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではないファイル *Web.config* で使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](../index.md)
