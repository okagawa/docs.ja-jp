---
description: "詳細情報: BC30154: <type1>'<typename>' はインターフェイス '<interfacename>' に対して '<membername>' を実装しなければなりません"
title: <type1>'<typename>' は、インターフェイス '<interfacename>' に対して '<membername>' を実装しなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: fc47aaef0477638e0e1a566bca23e9c35cf514f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641146"
---
# <a name="bc30154-type1typename-must-implement-membername-for-interface-interfacename"></a>BC30154: \<type1>'\<typename>' はインターフェイス '\<interfacename>' に対して '\<membername>' を実装しなければなりません

'\<typename>' は、インターフェイス '\<interfacename>' に対して '\<membername>' を実装しなければなりません。 プロパティの実装には、一致する 'ReadOnly'/'WriteOnly' 指定子が必要です。

 クラスまたは構造体では、インターフェイスを実装することが要求されますが、インターフェイスによって定義されるプロシージャ、プロパティ、またはイベントは実装しません。 インターフェイスのすべてのメンバーを実装する必要があります。

 **エラー ID:** BC30154

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. インターフェイスで定義されているものと同じ名前およびシグネチャのメンバーを宣言します。 少なくとも `End Function`、`End Sub`、または `End Property` ステートメントを含めてください。

2. `Function`、`Sub`、`Property`、または `Event` ステートメントの末尾に `Implements` 句を追加します。 次に例を示します。

    ```vb
    Public Event ItHappened() Implements IBaseInterface.ItHappened
    ```

3. プロパティを実装するときは、インターフェイス定義と同じ方法で `ReadOnly` または `WriteOnly` が使用されていることを確認します。

4. プロパティを実装する場合は、必要に応じて `Get` および `Set` プロシージャを宣言します。

## <a name="see-also"></a>関連項目

- [Implements ステートメント](../statements/implements-statement.md)
- [インターフェイス](../../programming-guide/language-features/interfaces/index.md)
