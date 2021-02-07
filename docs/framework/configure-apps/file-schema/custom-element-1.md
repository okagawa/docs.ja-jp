---
description: 詳細については、SingleTagSectionHandler のカスタム要素に関するページを参照してください。
title: SingleTagSectionHandler のカスタム要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 83022a1ebf295b89d5f868589e3d9a77c78e3fab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729980"
---
# <a name="custom-element-for-singletagsectionhandler"></a>SingleTagSectionHandler のカスタム要素

要素によって定義され、クラスを使用するカスタム構成セクションの設定を定義 \<section> し <xref:System.Configuration.SingleTagSectionHandler> ます。

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*

## <a name="syntax"></a>構文

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a>属性

属性と属性値はユーザーが定義します。

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>解説

要素は、 **\<sectionName>** [**\<section>**](section-element.md) 要素内のタグによって定義されたカスタム要素です [**\<configSections>**](configsections-element-for-configuration.md) 。 を呼び出すと、構成システムからオブジェクトが返され <xref:System.Collections.IDictionary> <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> ます。

## <a name="example"></a>例

次の例では、 **\<sampleSection>** クラスによって読み取られた設定を含むというカスタム要素を宣言してい <xref:System.Configuration.SingleTagSectionHandler> ます。

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではない *Web.config* ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
