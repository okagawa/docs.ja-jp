---
title: NETSDK1073:FrameworkReference は認識されませんでした
description: FrameworkReference が見つからない問題を解決する方法。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 2b2dbf2a0d3e13dca4fe634529b7951f2333ce28
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713029"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a>NETSDK1073:FrameworkReference は認識されませんでした

**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン

このエラーは、通常、SDK が検出できない特定の FrameworkReference のバージョンがあることを意味します。 *obj* と *bin* フォルダーを削除し、`dotnet restore` を実行して最新のターゲット パックを再ダウンロードしてみてください。

または、インストールに問題がある可能性があるため、最新バージョンの .NET と Visual Studio を使用していることを確認してください。
