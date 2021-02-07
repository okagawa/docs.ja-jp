---
description: '詳細情報: <clear> NameValueSectionHandler および DictionarySectionHandler の要素'
title: <clear> NameValueSectionHandler および DictionarySectionHandler の要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: 896aa7e8f0e3b41574538fcd9e4be9d6155da889
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699234"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<clear> NameValueSectionHandler および DictionarySectionHandler の要素

セクションで以前に定義したすべての設定を消去します。

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>構文

```xml
<clear />
```

## <a name="attributes"></a>属性

なし

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ------------|
| [**\<sectionName>** 要素](custom-element-2.md) | クラスおよびクラスを使用するカスタム構成セクションの設定を定義し <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> ます。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>解説

要素を使用して、 **\<clear>** 構成ファイル階層の上位レベルで定義されているすべての設定をアプリケーションから削除できます。

## <a name="example"></a>例

この例では、コンピューター構成ファイルとアプリケーション構成ファイルを定義し、 **\<clear>** アプリケーション構成ファイルで要素を使用して、マシン構成ファイルで以前に定義したセクションをクリアする方法を示します。

次のマシン構成ファイルのコードでは、セクションを宣言してい **\<mySection>** ます。

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

次のアプリケーション構成ファイルのコードは、からすべての設定を削除し **\<mySection>** ます。 アプリケーションは、 **\<mySection>** コンピューター構成ファイルのセクションので宣言された設定を取得できません。

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではないファイル *Web.config* で使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
