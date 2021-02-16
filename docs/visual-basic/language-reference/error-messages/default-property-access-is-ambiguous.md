---
description: "詳細情報: BC30686:Default プロパティ アクセスは、インターフェイス '<defaultpropertyname>' の継承インターフェイス メンバー '<interfacename1>' とインターフェイス '<defaultpropertyname>' の '<interfacename2>' との間で不適切です。"
title: Default プロパティ アクセスは、インターフェイス '<defaultpropertyname>' の継承インターフェイス メンバー '<interfacename1>' とインターフェイス '<defaultpropertyname>' の '<interfacename2>' との間で不適切です。
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: edf2823fb11184efb2c3101b81119ea1696234db
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455224"
---
# <a name="bc30686-default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>BC30686:Default プロパティ アクセスは、インターフェイス '\<defaultpropertyname>' の継承インターフェイス メンバー '\<interfacename1>' とインターフェイス '\<defaultpropertyname>' の '\<interfacename2>' との間で不適切です。

インターフェイスは、それぞれが同じ名前の既定のプロパティを宣言する 2 つのインターフェイスから継承します。 コンパイラは、この既定のプロパティへのアクセスを修飾なしで解決することはできません。 次に例を示します。

```vb
Public Interface Iface1
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface2
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface3
    Inherits Iface1, Iface2
End Interface
Public Class testClass
    Public Sub accessDefaultProperty()
        Dim testObj As Iface3
        Dim testInt As Integer = testObj(1)
    End Sub
End Class
```

`testObj(1)` を指定すると、コンパイラは、それを既定のプロパティに解決しようとします。 ただし、継承されたインターフェイスにより 2 つの既定のプロパティが考えられるため、コンパイラがこのエラーを通知します。

**エラー ID:** BC30686

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 同じ名前のメンバーを継承しないようにしてください。 前の例では、`testObj` が、メンバーのいずれか (たとえば `Iface2`) を必要としない場合は、次のように宣言します。

  ```vb
  Dim testObj As Iface1
  ```

  \- または -

- クラスに継承するインターフェイスを実装します。 その後、異なる名前を持つ継承されたプロパティのそれぞれを実装できます。 ただし、実装するクラスの既定のプロパティにすることができるのは、そのうちの 1 つだけです。 次に例を示します。

  ```vb
  Public Class useIface3
      Implements Iface3
      Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop
          ' Insert code to define Get and Set procedures for prop1.
      End Property
      Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop
          ' Insert code to define Get and Set procedures for prop2.
      End Property
  End Class
  ```

## <a name="see-also"></a>関連項目

- [インターフェイス](../../programming-guide/language-features/interfaces/index.md)
