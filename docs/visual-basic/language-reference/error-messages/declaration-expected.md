---
description: '詳細情報: BC30188:宣言が必要です。'
title: 宣言が必要です。
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: b86c182fb9dc8ab7d624833136f0e87b072aed92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796666"
---
# <a name="bc30188-declaration-expected"></a>BC30188:宣言が必要です。

代入ステートメントやループ ステートメントなどの非宣言ステートメントが、プロシージャの外側に記述されています。 プロシージャの外側で許可されるのは宣言のみです。

 または、プログラミング要素が、`Dim` や `Const` などの宣言キーワードを使用せずに宣言されています。

 **エラー ID:** BC30188

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 非宣言ステートメントをプロシージャの本体に移動します。

- 適切な宣言キーワードを使用して、宣言を開始します。

- 宣言キーワードのスペルが間違っていないことを確認します。

## <a name="see-also"></a>関連項目

- [手順](../../programming-guide/language-features/procedures/index.md)
- [Dim ステートメント](../statements/dim-statement.md)
