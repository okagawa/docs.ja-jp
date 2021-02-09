---
description: '詳細情報: BC36564:型引数をデリゲートから推論できませんでした'
title: 型引数をデリゲートから推論できませんでした
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 1a83ee64df4523cee87d0d677ddafaeadfe5543d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666265"
---
# <a name="bc36564-type-arguments-could-not-be-inferred-from-the-delegate"></a>BC36564:型引数をデリゲートから推論できませんでした

代入ステートメントは、 `AddressOf` を使用してジェネリック プロシージャのアドレスをデリゲートに割り当てますが、ジェネリック プロシージャに型引数を指定していません。

 通常、ジェネリック型を呼び出す場合は、ジェネリック型が定義する型パラメーターごとに型引数を指定します。 型引数を指定しない場合、コンパイラは型パラメーターに渡される型を推論しようとします。 コンテキストにコンパイラが型を推論するのに十分な情報が提供されていない場合は、エラーが生成されます。

 **エラー ID:** BC36564

## <a name="to-correct-this-error"></a>このエラーを解決するには

- ジェネリック プロシージャの型引数を `AddressOf` 式で指定します。

## <a name="see-also"></a>関連項目

- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [AddressOf 演算子](../operators/addressof-operator.md)
- [Generic Procedures in Visual Basic](../../programming-guide/language-features/data-types/generic-procedures.md)
- [型リスト](../statements/type-list.md)
- [拡張メソッド](../../programming-guide/language-features/procedures/extension-methods.md)
