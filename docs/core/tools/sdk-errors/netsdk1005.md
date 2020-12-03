---
title: NETSDK1005 および NETSDK1047:アセット ファイルにターゲットがありません
description: ターゲットがないアセット ファイルの問題を解決する方法。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 207c8b0274c13e7af594e05cfac2a95907f85b81
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717904"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a>NETSDK1005 および NETSDK1047:アセット ファイルにターゲットがありません

**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン

.NET SDK でエラー NETSDK1005 または NETSDK1047 が発生した場合、プロジェクトのアセット ファイルには、ターゲット フレームワークのいずれかに関する情報が存在しません。 これは通常、復元が実行され、不足しているターゲット値がプロジェクトの `TargetFrameworks` プロパティに含まれていることを確認することによって解決できます。

> [!NOTE]
> Visual Studio 16.8 プレビューのバージョンで .NET 5 preview 8 の初期ビルドが使用された場合の既知の問題があり、それがこのエラーの原因となりました。 具体的には、不足しているターゲットが `net5.0-windows7.0` または `net5.0` の場合は、Visual Studio と .NET 5 SDK の最新バージョンに更新したことを確認します。
