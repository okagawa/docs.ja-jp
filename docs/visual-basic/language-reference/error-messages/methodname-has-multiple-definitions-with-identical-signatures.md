---
description: '詳細情報: BC30269: メソッド "<methodname>" には、同じシグネチャを持つ複数の定義が含まれています。'
title: メソッド '<methodname>' には、同じシグネチャを持つ複数の定義が含まれています。
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 7364ee7a308fab96afce268ff0c92cd45717f1bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795808"
---
# <a name="bc30269-methodname-has-multiple-definitions-with-identical-signatures"></a>BC30269: メソッド "\<methodname>" には、同じシグネチャを持つ複数の定義が含まれています。

`Function` または `Sub` プロシージャ宣言で、前の宣言と同じプロシージャ名と引数リストを使用しています。 考えられる原因の 1 つは、元のプロシージャをオーバーロードしようとしたことです。 オーバーロードされたプロシージャには、異なる引数リストが必要です。

 **エラー ID:** BC30269

## <a name="to-correct-this-error"></a>このエラーを解決するには

- プロシージャ名または引数リストを変更するか、または重複する宣言を削除します。

## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [プロシージャのオーバーロードに関する注意事項](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
