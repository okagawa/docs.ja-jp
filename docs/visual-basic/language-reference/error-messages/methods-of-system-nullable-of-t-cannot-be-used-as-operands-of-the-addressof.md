---
description: "詳細情報: BC32126:'System.Nullable(Of T)' のメソッドを 'AddressOf' 演算子のオペランドとして使用することはできません。"
title: "'System.Nullable(Of T)' のメソッドを 'AddressOf' 演算子のオペランドとして使用することはできません。"
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 5ddf2f11bab3193423a3294a7f96afe68f0e5dce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795795"
---
# <a name="bc32126-methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>BC32126:'System.Nullable(Of T)' のメソッドを 'AddressOf' 演算子のオペランドとして使用することはできません。

ステートメントで、<xref:System.Nullable%601> 構造のプロシージャを表すオペランドで、`AddressOf` 演算子を使用します。

 **エラー ID:** BC32126

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `AddressOf` 句のプロシージャ名を、<xref:System.Nullable%601> のメンバーではないオペランドに置き換えます。

- 使用する <xref:System.Nullable%601> のメソッドをラップするクラスを記述します。 次の例では、`NullableWrapper` クラスで `GetValueOrDefault` という名前の新しいメソッドを定義しています。 この新しいメソッドは <xref:System.Nullable%601> のメンバーではないため、null 許容型のインスタンスである `nullInstance` に適用して `AddressOf` の引数を形成できます。

```vb
Module Module1

    Delegate Function Deleg() As Integer

    Sub Main()
        Dim nullInstance As New Nullable(Of Integer)(1)

        Dim del As Deleg

        ' GetValueOrDefault is a method of the Nullable generic
        ' type. It cannot be used as an operand of AddressOf.
        ' del = AddressOf nullInstance.GetValueOrDefault

        ' The following line uses the GetValueOrDefault method
        ' defined in the NullableWrapper class.
        del = AddressOf (New NullableWrapper(
            Of Integer)(nullInstance)).GetValueOrDefault

        Console.WriteLine(del.Invoke())
    End Sub

    Class NullableWrapper(Of T As Structure)
        Private m_Value As Nullable(Of T)

        Sub New(ByVal Value As Nullable(Of T))
            m_Value = Value
        End Sub

        Public Function GetValueOrDefault() As T
            Return m_Value.Value
        End Function
    End Class
End Module
```

## <a name="see-also"></a>関連項目

- <xref:System.Nullable%601>
- [AddressOf 演算子](../operators/addressof-operator.md)
- [null 許容値型](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
