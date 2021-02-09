---
description: '詳細情報: Of 句 (Visual Basic)'
title: Of 句
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: d6002041a2fe8db5b07e12e9e396a65fde30b716
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768845"
---
# <a name="of-clause-visual-basic"></a>Of 句 (Visual Basic)

`Of` 句が導入されています。これは、*ジェネリック* クラス、構造体、インターフェイス、デリゲート、またはプロシージャの *型パラメーター* を識別します。 ジェネリック型については、「[Visual Basic におけるジェネリック型](../../programming-guide/language-features/data-types/generic-types.md)」を参照してください。  
  
## <a name="using-the-of-keyword"></a>Of キーワードの使用  

 次のコード例では、`Of` キーワードを使用して、2 つの型パラメーターを受け取るクラスの概要を定義しています。 それは、<xref:System.IComparable> インターフェイスによって、`keyType` パラメーターを *制約* します。つまり、使用するコードで、<xref:System.IComparable> を実装する型引数を指定する必要があります。 これは、`add` プロシージャで <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> メソッドを呼び出せるようにするために必要です。 制約の詳細については、「 [Type List](type-list.md)」をご覧ください。  
  
```vb  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 前のクラス定義を完了したら、そこからさまざまな `dictionary` クラスを構築できます。 `entryType` および `keyType` に指定する型によって、クラスで保持されるエントリの型と、各エントリに関連付けられるキーの型が決まります。 制約のため、`keyType` に <xref:System.IComparable> を実装する型を指定する必要があります。  
  
 次のコード例では、`String` エントリを保持し、それぞれに `Integer` キーを関連付けるオブジェクトを作成しています。 `Integer` は <xref:System.IComparable> を実装しており、そのため、`keyType` の制約を満たします。  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 キーワード `Of` は次のコンテキストで使用できます。  
  
 [Class ステートメント](class-statement.md)  
  
 [Delegate ステートメント](delegate-statement.md)  
  
 [Function ステートメント](function-statement.md)  
  
 [Interface ステートメント](interface-statement.md)  
  
 [Structure ステートメント](structure-statement.md)  
  
 [Sub ステートメント](sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.IComparable>
- [型リスト](type-list.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [In](../modifiers/in-generic-modifier.md)
- [Out](../modifiers/out-generic-modifier.md)
