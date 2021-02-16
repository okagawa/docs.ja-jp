---
description: '詳細情報: 方法:2 つのオブジェクトが等しいかどうかをテストする (Visual Basic)'
title: '方法: 2 つのオブジェクトが等しいかどうかをテストする'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: a0136d9db487ad0ce70b9d55ff8ee014ec30b05a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435539"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>方法: 2 つのオブジェクトが等しいかどうかをテストする (Visual Basic)

オブジェクトを参照する 2 つの変数がある場合、`Is` または `IsNot` 演算子のいずれか、または両方を使用して、それらが同じインスタンスを参照するかどうかを判断できます。  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>2 つのオブジェクトが等しいかどうかをテストするには  
  
- 2 つの変数をオペランドとして、[Is Operator](../../../language-reference/operators/is-operator.md) または [IsNot Operator](../../../language-reference/operators/isnot-operator.md) を使用します。  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 2 つのオブジェクトが同じインスタンスを参照しているかどうかによって、特定のアクションを実行する場合があります。 前の例では、コントロール `c` をフォーム `f` のアクティブなコントロールと比較しています。 アクティブなコントロールがない場合、またはアクティブなコントロールはあるが `c` と同じコントロール インスタンスではない場合、`If` ステートメントは失敗し、プロシージャでは以降の処理を行わずに戻ります。  
  
 `Is` と `IsNot` のどちらを使用するかは、お客様の利便性の問題です。 指定された式について、読みやすいと思われる方とそうではない方がいるでしょう。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における比較演算子](comparison-operators.md)
