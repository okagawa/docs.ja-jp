---
title: 初期化子が必要です
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: cbe77bab3e4f8bf2094c70c1c16d95ee897c729e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163013"
---
# <a name="bc30996-initializer-expected"></a>BC30996:初期化子が必要です

次の例に示すように、初期化リストが空のオブジェクト初期化子を使用して、クラスのインスタンスを宣言しようとしました。

 `' Not valid.`

 `' Dim aStudent As New Student With {}`

 次の例に示すように、初期化子リストの少なくとも 1 つのフィールドまたはプロパティを初期化する必要があります。

 `Dim aStudent As New Student With {.year = "Senior"}`

 **エラー ID:** BC30996

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 初期化子の少なくとも 1 つのフィールドまたはプロパティを初期化するか、オブジェクト初期化子を使用しないようにしてください。

## <a name="see-also"></a>関連項目

- [オブジェクト初期化子: 名前付きの型と匿名型](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [方法: オブジェクト初期化子を使用してオブジェクトを宣言する](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
