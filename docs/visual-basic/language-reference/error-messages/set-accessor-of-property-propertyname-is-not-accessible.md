---
title: プロパティ '<propertyname>' の 'Set' アクセサーにアクセスできません。
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 3cf828eb5f11090a74a65388e2b89a191046a456
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162246"
---
# <a name="bc31102-set-accessor-of-property-propertyname-is-not-accessible"></a>BC31102:プロパティ '\<propertyname>' の 'Set' アクセサーにアクセスできません。

ステートメントは、プロパティの `Set` プロシージャにアクセスできない場合、プロパティの値を格納しようとします。

 [Set ステートメント](../statements/set-statement.md)がその [Property ステートメント](../statements/property-statement.md)よりも制限の厳しいアクセス レベルでマークされている場合は、プロパティ値を設定しようとすると、次のような場合は失敗する可能性があります。

- `Set` ステートメントが [Private](../modifiers/private.md) とマークされていて、呼び出し元のコードが、プロパティが定義されているクラスまたは構造体の外側にある。

- `Set` ステートメントが [Protected](../modifiers/protected.md) とマークされていて、呼び出し元のコードが、プロパティが定義されているクラスまたは構造体内にも、派生クラス内にもない。

- `Set` ステートメントが [Friend](../modifiers/friend.md) とマークされていて、呼び出し元のコードが、プロパティが定義されているアセンブリと同じアセンブリ内にない。

 **エラー ID:** BC31102

## <a name="to-correct-this-error"></a>このエラーを解決するには

- プロパティを定義するソース コードを制御できる場合は、プロパティ自体と同じアクセス レベルで `Set` プロシージャを宣言することを検討してください。

- プロパティを定義するソース コードを制御できない場合、またはプロパティ自体よりも `Set` プロシージャのアクセス レベルを制限する必要がある場合は、プロパティ値を設定するステートメントを、プロパティによりアクセスしやすいコードの領域に移動してみてください。

## <a name="see-also"></a>関連項目

- [Property プロシージャ](../../programming-guide/language-features/procedures/property-procedures.md)
- [方法: 複数のアクセス レベルを持つプロパティを宣言する](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
