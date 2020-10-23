---
title: "'<keyword>' は、インスタンス メソッド内でのみ有効です。"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: ad39ade294b362b20f2dfb93455445bf41d056cd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163325"
---
# <a name="bc30043-keyword-is-valid-only-within-an-instance-method"></a>BC30043: '\<keyword>' はインスタンス メソッド内でのみ有効です

`Me`、`MyClass`、および `MyBase` キーワードは、特定のクラス インスタンスを参照します。 それらを共有の `Function` または `Sub` プロシージャ内で使用することはできません。

"*エラー ID:* " * BC30043

## <a name="to-correct-this-error"></a>このエラーを解決するには

- プロシージャからキーワードを削除するか、プロシージャ宣言から `Shared` キーワードを削除します。

## <a name="see-also"></a>関連項目

- [オブジェクト変数の代入](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase、および MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [継承の基本](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
