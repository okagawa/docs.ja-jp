---
description: "詳細情報: BC33107:バイナリ 'If' 式の最初のオペランドは Null 許容または参照型である必要があります"
title: バイナリ 'If' 式の最初のオペランドは Null 許容または参照型である必要があります
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4a0037680e31a8220cb796e6d8f3215139e01b20
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796250"
---
# <a name="bc33107-first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>BC33107:バイナリ 'If' 式の最初のオペランドは Null 許容または参照型である必要があります

`If` 式は、2 つまたは 3 つの引数を取ることができます。 2 つの引数のみを送信する場合、最初の引数は参照型または Null 許容値型である必要があります。 最初の引数が `Nothing` 以外に評価される場合は、その値が返されます。 最初の引数が `Nothing` に評価される場合は、2 番目の引数が評価されて返されます。

 たとえば、次のコードには、3 つの引数を含むものと 2 つの引数を含むものの、2 つの `If` 式が含まれています。 これらの式は、同じ値を計算して返します。

```vb
' firstChoice is a nullable value type.
Dim firstChoice? As Integer = Nothing
Dim secondChoice As Integer = 1128
' If expression with three arguments.
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))
' If expression with two arguments.
Console.WriteLine(If(firstChoice, secondChoice))
```

 次の式では、このエラーが発生します。

```vb
Dim choice1 = 4
Dim choice2 = 5
Dim booleanVar = True

' Not valid.
'Console.WriteLine(If(choice1 < choice2, 1))
' Not valid.
'Console.WriteLine(If(booleanVar, "Test returns True."))
```

 **エラー ID:** BC33107

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 最初の引数が Null 許容値型または参照型になるようにコードを変更できない場合は、3 つの引数の `If` 式、または `If...Then...Else` ステートメントに変換することを検討してください。

```vb
Console.WriteLine(If(choice1 < choice2, 1, 2))
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))
```

## <a name="see-also"></a>関連項目

- [If 演算子](../operators/if-operator.md)
- [If...Then...Else ステートメント](../statements/if-then-else-statement.md)
- [null 許容値型](../../programming-guide/language-features/data-types/nullable-value-types.md)
