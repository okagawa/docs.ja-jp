---
title: "'Class' ステートメントの終わりには、対応する 'End Class' を指定しなければなりません。"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 6889e97aad913f6911ce438892752542de0d10f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163195"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a>BC30481:'Class' ステートメントの終わりには、対応する 'End Class' を指定しなければなりません。

`Class` は `Class` ブロックを開始するために使用します。ブロックの先頭にのみ指定でき、対応する`End Class` ステートメントでブロックを終えます。 `Class` ステートメントが重複しているか、`Class` ブロックの最後に `End Class` が使用されませんでした。

 **エラー ID:** BC30481

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 不要な `Class` ステートメントを見つけて削除します。

- 一致する `End Class` で `Class` ブロックを終了します。

## <a name="see-also"></a>関連項目

- [End \<keyword> ステートメント](../statements/end-keyword-statement.md)
- [Class ステートメント](../statements/class-statement.md)
