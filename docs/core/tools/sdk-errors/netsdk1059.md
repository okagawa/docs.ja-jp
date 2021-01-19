---
title: NETSDK1059:プロジェクトに古い .NET CLI ツールが含まれています
description: プロジェクトに古い .NET CLI ツールが含まれている問題を解決する方法。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1059
ms.openlocfilehash: bba5f4dafa346d81274541f3c40ecc5ed6fff8ab
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190326"
---
# <a name="netsdk1059-project-contains-obsolete-net-cli-tool"></a>NETSDK1059:プロジェクトに古い .NET CLI ツールが含まれています

**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン

.NET SDK によって警告 NETSDK1059 が発行される場合、プロジェクトには古い .NET CLI ツールが含まれています。 .NET Core 2.1 では、これらのツールは .NET SDK に含まれており、プロジェクトによって明示的に参照される必要はありません。 .NET Core 2.1 への移行の詳細については、[こちら](../../migration/20-21.md)を参照してください。
