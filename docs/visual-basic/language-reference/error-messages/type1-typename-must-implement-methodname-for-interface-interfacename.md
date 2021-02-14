---
description: "詳細情報: BC30149: <type1>'<typename>' はインターフェイス '<interfacename>' に対して '<methodname>' を実装しなければなりません"
title: <type1>'<typename>' は、インターフェイス '<interfacename>' に対して '<methodname>' を実装しなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 34635cbe5b8736d273d5972a1bb83aa3d975490b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675014"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a>BC30149: \<type1>'\<typename>' はインターフェイス '\<interfacename>' に対して '\<methodname>' を実装しなければなりません

クラスまたは構造体では、インターフェイスを実装することが要求されますが、インターフェイスによって定義されるプロシージャは実装しません。 インターフェイスのすべてのメンバーを実装する必要があります。

 **エラー ID:** BC30149

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. インターフェイスで定義されているものと同じ名前およびシグネチャを持つプロシージャを宣言します。 少なくとも `End Function` または `End Sub` ステートメントを含めてください。

2. `Function` または `Sub` ステートメントの末尾に `Implements` 句を追加します。 次に例を示します。

    ```vb
    Public Sub DoSomething() Implements IBaseInterface.DoSomething
    ```

## <a name="see-also"></a>関連項目

- [Implements ステートメント](../statements/implements-statement.md)
- [インターフェイス](../../programming-guide/language-features/interfaces/index.md)
