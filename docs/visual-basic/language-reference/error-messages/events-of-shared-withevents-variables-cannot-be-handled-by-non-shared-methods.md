---
description: '詳細情報: BC30594:共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。'
title: 共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f9e8bf6e0d365c4ee747deb6be0e809904d87117
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796419"
---
# <a name="bc30594-events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>BC30594:共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。

`Shared` 修飾子で宣言される変数は共有変数です。 共有変数は、格納場所を 1 つだけ識別します。 `WithEvents` 修飾子で宣言される変数は、変数が属する型によって、変数で起動するイベントのセットが処理されることをアサートします。 変数に値が代入されると、`WithEvents` 宣言によって作成されるプロパティは、既存のイベント ハンドラーをアンフックし、`Add` メソッドを使用して新しいイベント ハンドラーをフックします。

 **エラー ID:** BC30594

## <a name="to-correct-this-error"></a>このエラーを解決するには

- イベント ハンドラー `Shared` を宣言します。

## <a name="see-also"></a>関連項目

- [Shared](../modifiers/shared.md)
- [WithEvents](../modifiers/withevents.md)
