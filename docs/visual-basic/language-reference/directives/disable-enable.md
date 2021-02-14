---
description: '詳細情報: #Disable および #Enable ディレクティブ (Visual Basic)'
title: Enable および Disable ディレクティブ
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: d600cc959639a3f70bca5678fbc81aae0806c9cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797264"
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
