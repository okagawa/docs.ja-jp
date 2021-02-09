---
description: '詳細情報: Optional (Visual Basic)'
title: Optional
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: d9a61371364d87745203363dbc0a641cec9660a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666083"
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)

プロシージャが呼び出されるときにプロシージャ引数が省略可能であることを示します。

## <a name="remarks"></a>Remarks

省略可能なパラメーターごとに、そのパラメーターの既定値として定数式を指定する必要があります。 式が [Nothing](../nothing.md) に評価される場合は、値データ型の既定値がパラメーターの既定値として使用されます。

パラメーター リストに省略可能なパラメーターが含まれている場合は、その後に続くすべてのパラメーターも省略可能である必要があります。

`Optional` 修飾子は、次のコンテキストで使用できます。

- [Declare ステートメント](../statements/declare-statement.md)

- [Function ステートメント](../statements/function-statement.md)

- [Property ステートメント](../statements/property-statement.md)

- [Sub ステートメント](../statements/sub-statement.md)

> [!NOTE]
> 省略可能なパラメーターの有無にかかわらず、プロシージャを呼び出すときは、位置または名前によって引数を渡すことができます。 詳細については、「[位置と名前による引数渡し](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)」を参照してください。

> [!NOTE]
> オーバーロードを使用して省略可能なパラメーターを持つプロシージャを定義することもできます。 省略可能なパラメーターが 1 つあるとすると、パラメーターを受け取る場合と受け取らない場合の、2 つのオーバーロードされたバージョンのプロシージャを定義できます。 詳細については、「 [Procedure Overloading](../../programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。

## <a name="example"></a>例

次の例では、省略可能なパラメーターがあるプロシージャを定義しています。

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a>例

次の例では、位置で渡される引数と名前で渡される引数を使用してプロシージャを呼び出す方法を示します。 このプロシージャには、2 つの省略可能なパラメーターがあります。

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a>関連項目

- [パラメーター リスト](../statements/parameter-list.md)
- [省略可能なパラメーター](../../programming-guide/language-features/procedures/optional-parameters.md)
- [キーワード](../keywords/index.md)
