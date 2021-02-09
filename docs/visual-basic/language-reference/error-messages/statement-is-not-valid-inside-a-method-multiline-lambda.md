---
description: '詳細情報: BC30024:メソッドや複数行のラムダの内部では有効でないステートメントです。'
title: メソッドや複数行のラムダの内部では有効でないステートメントです。
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: c70e5563ab8c161966cd9790ae1f192fa5d50b17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731176"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a>BC30024:メソッドや複数行のラムダの内部では有効でないステートメントです。

ステートメントは、`Sub`、`Function`、プロパティ `Get`、またはプロパティ `Set` プロシージャ内で無効です。 一部のステートメントは、モジュール レベルまたはクラス レベルで配置できます。 `Option Strict` などの他のものは、名前空間レベルで、他のすべての宣言の前に配置する必要があります。

 **エラー ID:** BC30024

## <a name="to-correct-this-error"></a>このエラーを解決するには

- プロシージャからステートメントを削除します。

## <a name="see-also"></a>関連項目

- [Sub ステートメント](../statements/sub-statement.md)
- [Function ステートメント](../statements/function-statement.md)
- [Get ステートメント](../statements/get-statement.md)
- [Set ステートメント](../statements/set-statement.md)
