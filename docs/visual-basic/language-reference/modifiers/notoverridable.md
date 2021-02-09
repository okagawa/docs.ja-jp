---
description: '詳細情報: NotOverridable (Visual Basic)'
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: f0363024aacc1ed6ab9d8820cc965b5b71e557b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666096"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)

派生クラス内のプロパティまたはプロシージャをオーバーライドできないことを示します。  
  
## <a name="remarks"></a>Remarks  

 `NotOverridable` 修飾子は、派生クラス内のプロパティまたはメソッドがオーバーライドされるのを防ぎます。  [Overridable](overridable.md) 修飾子を使用すると、クラス内のプロパティまたはメソッドを派生クラスでオーバーライドできます。 詳細については、「[継承の基本](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。  
  
 `Overridable` または `NotOverridable` 修飾子が指定されていない場合、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。 プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定の設定は `Overridable` であり、そうでない場合は `NotOverridable` です。  
  
 オーバーライドできない要素は、*シールド* 要素と呼ばれることもあります。  
  
 `NotOverridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。 `NotOverridable` は、別のプロパティまたはプロシージャをオーバーライドするプロパティまたはプロシージャでのみ、つまり `Overrides` との組み合わせでのみ指定できます。  
  
## <a name="combined-modifiers"></a>結合された修飾子  

 `Private` メソッドに `Overridable` または `NotOverridable` を指定することはできません。  
  
 同じ宣言内で `NotOverridable` を `MustOverride`、`Overridable`、または `Shared` と共に指定することはできません。  
  
## <a name="usage"></a>使用方法  

 `NotOverridable` 修飾子は、次のコンテキストで使用できます。  
  
 [Function ステートメント](../statements/function-statement.md)  
  
 [Property ステートメント](../statements/property-statement.md)  
  
 [Sub ステートメント](../statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [修飾子](index.md)
- [継承の基本](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [Overridable](overridable.md)
- [Overrides](overrides.md)
- [キーワード](../keywords/index.md)
- [Visual Basic におけるシャドウ](../../programming-guide/language-features/declared-elements/shadowing.md)
