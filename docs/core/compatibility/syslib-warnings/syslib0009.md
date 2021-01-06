---
title: SYSLIB0009 警告
description: コンパイル時の警告 SYSLIB0009 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 922fcc30b2b1577976e4e88e3f7631e19d4b2cce
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596359"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a>SYSLIB0009:AuthenticationManager 認証および PreAuthenticate メソッドはサポートされていません

.NET 5.0 以降、次の API は古いものとしてマークされています。 これらの API を使用すると、コンパイル時に警告 `SYSLIB0009` が生成されます。

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a>警告を非表示にする

コードを変更できない場合、`#pragma` ディレクティブか `<NoWarn>` プロジェクト設定で警告を非表示にできます。 例については、「[警告を表示しない](../syslib-obsoletions.md#suppress-warnings)」を参照してください。
