---
title: NETSDK1022:重複する項目が含まれていました。
description: 既定のインクルードに基づいて重複する項目メッセージを解決する方法。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: bc803f5316bf09c12c563f1a63b8385d1be4e9ce
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506637"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022:重複する項目が含まれていました。

**この記事の対象:**  ✔️ .NET 2.1.100 SDK 以降のバージョン

Visual Studio 2017 または MSBuild バージョン 15.3 以降、.NET SDK に既定でプロジェクト ディレクトリの項目が自動的に含まれています。  これには、`Compile` および `Content` のターゲットが含まれます。  これにより、プロジェクト ファイルの大部分がクリーンアップされ、複雑さが軽減されます。

適切なプロパティを false に設定すると、以前の動作に戻すことができます。

`Compile` 項目の例:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
