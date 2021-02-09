---
description: '詳細情報: MustOverride (Visual Basic)'
title: New
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: df7200a7f7ec4bfda34765747d6318bc50a38dd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774526"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)

プロパティやプロシージャがこのクラスで実装されておらず、派生クラスでオーバーライドされないと使用できないことを示します。  
  
## <a name="remarks"></a>Remarks  

 `MustOverride` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。 `MustOverride` を指定するプロパティまたはプロシージャはクラスのメンバーである必要があり、クラスは [MustInherit](mustinherit.md) としてマークする必要があります。  
  
## <a name="rules"></a>ルール  
  
- **不完全な宣言。** `MustOverride` を指定する場合、`End Function`、`End Property`、または `End Sub` ステートメントでも、プロパティまたはプロシージャに追加のコード行を指定しません。  
  
- **結合された修飾子。** 同じ宣言内で `MustOverride` を `NotOverridable`、`Overridable`、または `Shared` と共に指定することはできません。  
  
- **シャドウとオーバーライド。** シャドウとオーバーライドは、どちらも継承された要素を再定義しますが、その方法は大きく異なります。 詳細については、「[Visual Basic におけるシャドウ](../../programming-guide/language-features/declared-elements/shadowing.md)」を参照してください。  
  
- **代替用語。** オーバーライド以外で使用できない要素は、*純粋仮想* 要素と呼ばれることもあります。  
  
 `MustOverride` 修飾子は、次のコンテキストで使用できます。  
  
 [Function ステートメント](../statements/function-statement.md)  
  
 [Property ステートメント](../statements/property-statement.md)  
  
 [Sub ステートメント](../statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [NotOverridable](notoverridable.md)
- [Overridable](overridable.md)
- [Overrides](overrides.md)
- [MustInherit](mustinherit.md)
- [キーワード](../keywords/index.md)
- [Visual Basic におけるシャドウ](../../programming-guide/language-features/declared-elements/shadowing.md)
