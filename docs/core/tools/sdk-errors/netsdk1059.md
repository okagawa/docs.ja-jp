---
title: NETSDK1059:プロジェクトに古い .NET CLI ツールが含まれています
description: プロジェクトに古い .NET CLI ツールが含まれている問題を解決する方法。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1059
ms.openlocfilehash: b80f42495e1aff8d37008946f10f68c195d5a9ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713120"
---
# <a name="netsdk1059-project-contains-obsolete-net-cli-tool"></a>NETSDK1059:プロジェクトに古い .NET CLI ツールが含まれています

**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン

.NET SDK によって警告 NETSDK1059 が発行される場合、プロジェクトには古い .NET CLI ツールが含まれています。 .NET Core 2.1 では、これらのツールは .NET SDK に含まれており、プロジェクトによって明示的に参照される必要はありません。 .NET Core 2.1 への移行の詳細については、[こちら](https://aka.ms/dotnetclitools-in-box)を参照してください。
