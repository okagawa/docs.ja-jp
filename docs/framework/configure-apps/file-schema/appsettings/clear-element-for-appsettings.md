---
description: '詳細情報: <clear> の要素 <appSettings>'
title: <appSettings> の <clear> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 88c6a02441c038619cb74947c024de7712189915
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699338"
---
# <a name="clear-element-for-appsettings"></a>\<appSettings> の \<clear> 要素

カスタムアプリケーション設定をクリアします。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>構文

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>属性

なし

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | ファイルパス、XML Web サービス Url、その他のカスタムアプリケーション構成情報などのカスタムアプリケーション設定が含まれます。 |

## <a name="child-elements"></a>子要素

なし

## <a name="example"></a>例

次の例は、カスタム構成設定をクリアする方法を示しています。

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](../index.md)
