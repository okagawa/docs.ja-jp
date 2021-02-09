---
description: '詳細情報: Overridable (Visual Basic)'
title: Overridable
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: acbbd715113c836a3fb7f8a88bf74307c38ac682
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730500"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)

プロパティまたはプロシージャが派生クラスで同じ名前のプロパティまたはプロシージャによってオーバーライドできることを示します。  
  
## <a name="remarks"></a>Remarks  

 `Overridable` 修飾子を使用すると、クラス内のプロパティまたはメソッドを派生クラスでオーバーライドできます。 [NotOverridable](notoverridable.md) 修飾子は、派生クラス内のプロパティまたはメソッドがオーバーライドされるのを防ぎます。  詳細については、「[継承の基本](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。  
  
 `Overridable` または `NotOverridable` 修飾子が指定されていない場合、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。 プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定の設定は `Overridable` であり、そうでない場合は `NotOverridable` です。  
  
 シャドウまたはオーバーライドによって継承された要素を再定義できますが、この 2 つの方法には大きな違いがあります。 詳細については、「[Visual Basic におけるシャドウ](../../programming-guide/language-features/declared-elements/shadowing.md)」を参照してください。  
  
 オーバーライドできる要素は、*仮想* 要素と呼ばれることもあります。 オーバーライドは可能でも、必要がない場合は、*具象* 要素と呼ばれることもあります。  
  
 `Overridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。  
  
## <a name="combined-modifiers"></a>結合された修飾子  

 `Private` メソッドに `Overridable` または `NotOverridable` を指定することはできません。  
  
 同じ宣言内で `Overridable` を `MustOverride`、`NotOverridable`、または `Shared` と共に指定することはできません。  
  
 オーバーライドする要素は暗黙的にオーバーライド可能であるため、`Overridable` と `Overrides` を結合することはできません。  
  
## <a name="usage"></a>使用方法  

 `Overridable` 修飾子は、次のコンテキストで使用できます。  
  
 [Function ステートメント](../statements/function-statement.md)  
  
 [Property ステートメント](../statements/property-statement.md)  
  
 [Sub ステートメント](../statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [修飾子](index.md)
- [継承の基本](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Overrides](overrides.md)
- [キーワード](../keywords/index.md)
- [Visual Basic におけるシャドウ](../../programming-guide/language-features/declared-elements/shadowing.md)
