---
title: SYSLIB0012 警告
description: コンパイル時の警告 SYSLIB0012 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dc139d5c5cb6d6a34d161147b350b3324d15117e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440583"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a>SYSLIB0012:Assembly.CodeBase と Assembly.EscapedCodeBase は旧型式

.NET 5.0 以降、次の API は古いものとしてマークされています。 これらをコードで使用すると、コンパイル時に警告 `SYSLIB0012` が生成されます。

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a>回避策

代わりに、<xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> を使用してください。

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]
