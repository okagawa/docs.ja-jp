---
description: '詳細情報: 方法:属性を使用して C/C++ の共用体を作成する (Visual Basic)'
title: '方法: 属性を使用して C/C++ の共用体を作成する'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: 10717ec97efe866f4c3993cc26789f29d97b148a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437749"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>方法: 属性を使用して C/C++ の共用体を作成する (Visual Basic)

属性を使用すると、構造体のメモリ内での配置をカスタマイズできます。 たとえば、`StructLayout(LayoutKind.Explicit)` 属性と `FieldOffset` 属性を使用すると、C/C++ の共用体と呼ばれるものを作成できます。

## <a name="example"></a>例

このコード セグメントでは、`TestUnion` のすべてのフィールドがメモリ内の同じ場所で開始されます。

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a>例

次の例でも、明示的に設定されたさまざまな場所でフィールドが開始されます。

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

2 つの整数フィールド、`i1` および `i2` は、`lg` と同じメモリ位置を共有します。 このような構造体配置の制御は、プラットフォームを呼び出すときに便利です。

## <a name="see-also"></a>関連項目

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Visual Basic プログラミング ガイド](../../index.md)
- [属性](../../../../standard/attributes/index.md)
- [リフレクション (Visual Basic)](../reflection.md)
- [属性 (Visual Basic)](../../../language-reference/attributes.md)
- [カスタム属性の作成 (Visual Basic)](creating-custom-attributes.md)
- [リフレクションを使用した属性へのアクセス (Visual Basic)](accessing-attributes-by-using-reflection.md)
