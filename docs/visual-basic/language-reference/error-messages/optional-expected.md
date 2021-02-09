---
description: "詳細情報: BC30202:'Optional' が必要です。"
title: "'Optional' が必要です。"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 543dbf6226d4d298d46764ee506b55e770c91604
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795548"
---
# <a name="bc30202-optional-expected"></a>BC30202:'Optional' が必要です。

プロシージャ宣言内の省略可能な引数の後に必須の引数があります。 省略可能な引数の後の引数もすべて、省略可能である必要があります。

 **エラー ID:** BC30202

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 引数が必須と想定される場合は、引数リストの最初の省略可能な引数の前に移動します。

- 引数が省略可能と想定される場合は、`Optional` キーワードを使用します。

## <a name="see-also"></a>関連項目

- [省略可能なパラメーター](../../programming-guide/language-features/procedures/optional-parameters.md)
