---
description: '詳細情報: BC32005:If ステートメント行の外側でステートメント ブロックを終了することはできません。'
title: If ステートメント行の外側でステートメント ブロックを終了することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: afe856b2c2ea3fa1db029d35c5b876f5d67da411
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731141"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>BC32005:If ステートメント行の外側でステートメント ブロックを終了することはできません。

単一行の `If` ステートメントにコロン (:) で区切られた複数のステートメントが含まれていて、そのうちの 1 つが、単一行の `If` の外側にある制御ブロックの `End` ステートメントです。 単一行の `If` ステートメントで、`End If` ステートメントが使用されません。

 **エラー ID:** BC32005

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 単一行の `If` ステートメントを、`End If` ステートメントが含まれている制御ブロックの外側に移動します。

## <a name="see-also"></a>関連項目

- [If...Then...Else ステートメント](../statements/if-then-else-statement.md)
