---
title: SYSLIB0012 警告
description: コンパイル時の警告 SYSLIB0012 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 9b3fa94029efb2343e6dbbeb3ae36195f0956523
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596300"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a>SYSLIB0012:Assembly.CodeBase と Assembly.EscapedCodeBase は旧型式

.NET 5.0 以降、次の API は古いものとしてマークされています。 これらをコードで使用すると、コンパイル時に警告 `SYSLIB0012` が生成されます。

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a>回避策

代わりに、<xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> を使用してください。

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]
