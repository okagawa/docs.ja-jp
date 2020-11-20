---
title: SYSLIB0009 警告
description: コンパイル時の警告 SYSLIB0009 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 47b4f595a54800370da90f61d838c665df8b6091
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439977"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a>SYSLIB0009:AuthenticationManager 認証および PreAuthenticate メソッドはサポートされていません

.NET 5.0 以降、次の API は古いものとしてマークされています。 これらの API を使用すると、コンパイル時に警告 `SYSLIB0009` が生成されます。

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a>警告を非表示にする

コードを変更できない場合、`#pragma` ディレクティブか `<NoWarn>` プロジェクト設定で警告を非表示にできます。 例については、「[警告を表示しない](syslib-obsoletions.md#suppress-warnings)」を参照してください。
