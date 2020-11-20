---
title: SYSLIB0008 警告
description: コンパイル時の警告 SYSLIB0008 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 22ac5b4c5f57ec3f92585ee8d1f8cf278a15dbb0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440596"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a>SYSLIB0008: CreatePdbGenerator はサポートされていません

.NET 5.0 以降、<xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API は古いものとしてマークされています。 この API を使用すると、コンパイル時に警告 `SYSLIB0008` が生成されます。

## <a name="suppress-the-warning"></a>警告を非表示にする

コードを変更できない場合、`#pragma` ディレクティブか `<NoWarn>` プロジェクト設定で警告を非表示にできます。 例については、「[警告を表示しない](syslib-obsoletions.md#suppress-warnings)」を参照してください。
