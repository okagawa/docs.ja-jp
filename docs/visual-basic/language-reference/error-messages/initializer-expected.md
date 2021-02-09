---
description: '詳細情報: BC30996:初期化子が必要です'
title: 初期化子が必要です
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: a9859dc319ec53cb42785d71b21447a097ce30f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796055"
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
