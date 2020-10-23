---
title: If ステートメント行の外側でステートメント ブロックを終了することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 4fd7577accd0b312ee1e3d2d990d256514d5f5f6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161336"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>BC32005:If ステートメント行の外側でステートメント ブロックを終了することはできません。

単一行の `If` ステートメントにコロン (:) で区切られた複数のステートメントが含まれていて、そのうちの 1 つが、単一行の `If` の外側にある制御ブロックの `End` ステートメントです。 単一行の `If` ステートメントで、`End If` ステートメントが使用されません。

 **エラー ID:** BC32005

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 単一行の `If` ステートメントを、`End If` ステートメントが含まれている制御ブロックの外側に移動します。

## <a name="see-also"></a>関連項目

- [If...Then...Else ステートメント](../statements/if-then-else-statement.md)
