---
description: '詳細情報: WithEvents (Visual Basic)'
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: b27f84fe54aaa10bc9b2359cd74fad3d3ace1ad5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674767"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)

1 つ以上の宣言されたメンバー変数が、イベントを発生させる可能性のあるクラスのインスタンスを参照していることを示します。

## <a name="remarks"></a>Remarks

変数が `WithEvents` を使用して定義されている場合は、メソッドが `Handles` キーワードを使用して変数のイベントを処理するように、宣言によって指定できます。

`WithEvents` は、クラスまたはモジュール レベルでのみ使用できます。 つまり、`WithEvents` 変数の宣言コンテキストはクラスまたはモジュールにする必要があり、ソース ファイル、名前空間、構造体、またはプロシージャにすることはできません。

構造体メンバーでは `WithEvents` は使用できません。

`WithEvents` では、配列ではなく個々の変数のみを宣言できます。

## <a name="rules"></a>ルール

**要素型。** オブジェクト変数として `WithEvents` 変数を宣言して、クラス インスタンスを受け入れられるようにする必要があります。 C++ では、これらを `Object` として宣言することはできません。 イベントを発生可能な特定のクラスとして宣言する必要があります。

`WithEvents` 修飾子は、次のコンテキストで使用できます。[Dim ステートメント](../statements/dim-statement.md)

## <a name="example"></a>例

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>関連項目

- [Handles](../statements/handles-clause.md)
- [キーワード](../keywords/index.md)
- [イベント](../../programming-guide/language-features/events/index.md)
