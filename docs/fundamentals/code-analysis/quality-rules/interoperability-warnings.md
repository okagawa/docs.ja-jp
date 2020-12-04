---
title: 移植性と相互運用性の規則 (コード分析)
description: コード分析規則の移植性と相互運用性の規則について
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2020
ms.locfileid: "96591195"
---
# <a name="portability-and-interoperability-rules"></a>移植性と相互運用性の規則

移植性ルールは、異なるプラットフォーム間での移植性をサポートします。 相互運用性規則は、COM クライアントとの対話をサポートします。

## <a name="in-this-section"></a>このセクションの内容

| ルール | 説明 |
| - | - |
| [CA1401: P/Invoke を表示できません](ca1401.md) | パブリック型のパブリックメソッドまたはプロテクトメソッドには System.Runtime.InteropServices.DllImportAttribute 属性があります (Visual Basic で Declare キーワードによっても実装されています)。 このようなメソッドは公開しないでください。 |
| [CA1416:プラットフォームの互換性を検証する](ca1416.md) | コンポーネントでプラットフォームに依存する Api を使用すると、コードがすべてのプラットフォームで動作しなくなります。 |
| [CA1417: `OutAttribute` P/invoke に文字列パラメーターを使用しません](ca1417.md) | で値によって渡される文字列パラメーター `OutAttribute` は、文字列がインターン文字列である場合、ランタイムを不安定にする可能性があります。 |
