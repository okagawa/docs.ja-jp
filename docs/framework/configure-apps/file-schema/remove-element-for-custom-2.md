---
description: '詳細情報: <remove> NameValueSectionHandler および DictionarySectionHandler の要素'
title: <remove> NameValueSectionHandler および DictionarySectionHandler の要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: bf1434b257aa014c8f46e34f2d57d109bd510452
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740081"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<remove> NameValueSectionHandler および DictionarySectionHandler の要素

以前に定義した設定を削除します。

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>構文

```xml
<add remove="key" />
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **key**   | 必須の属性です。<br><br>削除する設定の名前を指定します。 |

## <a name="parent-element"></a>親要素

| 要素 | 説明 |
| ------- | ------------|
| [**\<sectionName>** 要素](custom-element-2.md) | クラスおよびクラスを使用するカスタム構成セクションの設定を定義し <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> ます。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>解説

要素を使用して、 **\<remove>** 構成ファイル階層の上位レベルで定義されているアプリケーションから設定を削除できます。

## <a name="example"></a>例

次の例は、 **\<remove>** アプリケーション構成ファイルで要素を使用して、マシン構成ファイルで以前に定義した設定を削除する方法を示しています。

次のマシン構成ファイルのコードでは、セクションを宣言 **\<mySection>** し、2つの設定 ( `key1` と `key2` ) を追加します。

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

次のアプリケーション構成ファイルのコードは、から設定を削除し `key2` **\<mySection>** ます。

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではないファイル *Web.config* で使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
