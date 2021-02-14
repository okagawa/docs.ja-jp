---
description: "詳細情報: BC30014: '#ElseIf' の前には、対応する '#If' または '#ElseIf' が必要です"
title: "'#Else' の前には、対応する '#If' または '#ElseIf' が必要です。"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 5eeb9c2fc0fd7267d95a8713a7071cd08788e48b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796562"
---
# <a name="bc30014-elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>BC30014: '#ElseIf' の前には、対応する '#If' または '#ElseIf' が必要です

`#ElseIf` は条件付きコンパイル ディレクティブです。 `#If` または `#ElseIf` 句の前には、対応する `#ElseIf` が必要です。

 **エラー ID:** BC30014

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 先行する `#If` または `#ElseIf` が、中間の条件付きコンパイル ブロックまたは正しくない位置にある `#ElseIf` によって、この `#End If` と分離されていないことを確認します。

2. `#ElseIf` の前に `#Else` ディレクティブがある場合は、`#Else` を削除するか、`#ElseIf` に変更します。

3. 他のすべての順序が正しい場合、 `#If` ディレクティブを条件付きコンパイル ブロックの先頭に追加します。

## <a name="see-also"></a>関連項目

- [#If...Then...#Else ディレクティブ](../directives/if-then-else-directives.md)
