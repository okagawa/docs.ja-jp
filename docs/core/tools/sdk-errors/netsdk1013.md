---
title: NETSDK1013:TargetFramework 値が認識されませんでした。
description: 有効な TargetFramework 値を決定し、設定する方法
author: marcpop
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1013
ms.openlocfilehash: bcaed878b663f8bc957e8469ffd78caa9babf710
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445683"
---
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a>NETSDK1013:TargetFramework 値が認識されませんでした

**この記事の対象:**  ✔️ .NET 3.1.100 SDK 以降のバージョン

SDK によって、`<TargetFramework>` または `<TargetFrameworks>` のプロジェクト ファイルで指定された値が既知の値に解析されます。  値が認識されない場合、`TargetFrameworkIdentifier` または `TargetFrameworkVersion` 値は空の文字列か `Unsupported` に設定されることがあります。

これを解決するには、[サポートされているフレームワーク](../../../standard/frameworks.md)の一覧で `TargetFramework` 値の綴りを確認します。
プロジェクト ファイルで直接、`TargetFrameworkIdentifier` プロパティと `TargetFrameworkVersion` プロパティを設定することもできます。

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```
