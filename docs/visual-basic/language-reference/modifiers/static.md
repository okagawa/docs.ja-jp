---
description: '詳細情報: Static (Visual Basic)'
title: Static
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 03c2e3f64ac9052a0c604b8bc34782af16edbf34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700742"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)

1 つ以上の宣言されているローカル変数が存在し続け、それらが宣言されているプロシージャの終了後もその最新の値が保持されるように指定します。  
  
## <a name="remarks"></a>Remarks  

 通常、プロシージャ内のローカル変数は、プロシージャが停止するとすぐに存在しなくなります。 静的変数は存在し続け、その最新の値が保持されます。 次回にコードでプロシージャを呼び出したときに、変数は再初期化されず、それに代入された最新の値も保持されます。 静的変数は、それが定義されているクラスまたはモジュールの有効期間にわたって存在し続けます。  
  
## <a name="rules"></a>ルール  
  
- **宣言コンテキスト。** `Static` は、ローカル変数にのみ使用できます。 つまり、`Static` 変数の宣言コンテキストは、プロシージャまたはプロシージャ内のブロックにする必要があり、ソース ファイル、名前空間、クラス、構造体、またはモジュールにすることはできません。  
  
     構造体プロシージャ内で `Static` を使用することはできません。  
  
- `Static` ローカル変数のデータ型は推論できません。 詳細については、「[ローカル型の推論](../../programming-guide/language-features/variables/local-type-inference.md)」を参照してください。  
  
- **結合された修飾子。** 同じ宣言内で `Static` を `ReadOnly`、`Shadows`、または `Shared` と共に指定することはできません。  
  
## <a name="behavior"></a>動作  

 `Shared` プロシージャで静的変数を宣言する場合、アプリケーション全体で使用できる静的変数のコピーは 1 つだけです。 クラスのインスタンスを指す変数ではなく、クラス名を使用して `Shared` プロシージャを呼び出します。  
  
 `Shared` ではないプロシージャで静的変数を宣言すると、クラスの各インスタンスで使用できる変数のコピーは 1 つだけです。 非共有プロシージャを呼び出すには、クラスの特定のインスタンスを指す変数を使用します。  
  
## <a name="example"></a>例  

 次の例は、`Static` の使い方を示しています。  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static` 変数の `totalSales` は、1 回だけ 0 に初期化されます。 `updateSales` を入力するたびに、`totalSales` には、それに対して計算した最新の値が引き続き含まれます。  
  
 `Static` 修飾子は、次のコンテキストで使用できます。  
  
 [Dim ステートメント](../statements/dim-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Shadows](shadows.md)
- [Shared](shared.md)
- [Visual Basic における有効期間](../../programming-guide/language-features/declared-elements/lifetime.md)
- [変数宣言](../../programming-guide/language-features/variables/variable-declaration.md)
- [構造体](../../programming-guide/language-features/data-types/structures.md)
- [ローカル型の推論](../../programming-guide/language-features/variables/local-type-inference.md)
- [クラスとオブジェクト](../../programming-guide/language-features/objects-and-classes/index.md)
