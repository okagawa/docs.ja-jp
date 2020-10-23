---
title: メソッド '<methodname>' には、同じシグネチャを持つ複数の定義が含まれています。
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 663b22421d1a0e401cfb3c135c99bd097163a78b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160367"
---
# <a name="bc30269-methodname-has-multiple-definitions-with-identical-signatures"></a>BC30269: メソッド "\<methodname>" には、同じシグネチャを持つ複数の定義が含まれています。

`Function` または `Sub` プロシージャ宣言で、前の宣言と同じプロシージャ名と引数リストを使用しています。 考えられる原因の 1 つは、元のプロシージャをオーバーロードしようとしたことです。 オーバーロードされたプロシージャには、異なる引数リストが必要です。

 **エラー ID:** BC30269

## <a name="to-correct-this-error"></a>このエラーを解決するには

- プロシージャ名または引数リストを変更するか、または重複する宣言を削除します。

## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [プロシージャのオーバーロードに関する注意事項](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
