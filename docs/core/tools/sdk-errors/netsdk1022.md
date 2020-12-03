---
title: NETSDK1022:重複する項目が含まれていました。
description: 既定のインクルードに基づいて重複する項目メッセージを解決する方法。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: c2bdbbb5503e5e4f6e6826f95f5a2cb08c908ceb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717872"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022:重複する項目が含まれていました。

**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン

Visual Studio 2017 または MSBuild バージョン 15.3 以降、.NET SDK に既定でプロジェクト ディレクトリの項目が自動的に含まれています。  これには、`Compile` および `Content` のターゲットが含まれます。  これにより、プロジェクト ファイルの大部分がクリーンアップされ、複雑さが軽減されます。

適切なプロパティを false に設定すると、以前の動作に戻すことができます。

`Compile` 項目の例:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
