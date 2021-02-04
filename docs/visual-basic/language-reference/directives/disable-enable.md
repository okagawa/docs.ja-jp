---
title: Enable および Disable ディレクティブ
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: 3104b25c903465f3a650304f477b25a74591c8ba
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217272"
---
# <a name="disable-and-enable-directives-visual-basic"></a>#Disable および #Enable ディレクティブ (Visual Basic)

`#Disable` および `#Enable` ディレクティブは Visual Basic ソース コード コンパイラ ディレクティブです。 これらは、コードの領域に対して特定の警告を無効にしたり、再度有効にするために使用されます。

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

警告コードのコンマ区切りリストを無効および有効にすることもできます。

## <a name="see-also"></a>関連項目

- [Visual Basic の言語リファレンス](../index.md)
- [コード分析の警告を抑制する方法](../../../fundamentals/code-analysis/suppress-warnings.md)
