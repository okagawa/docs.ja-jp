---
title: カスタム属性の作成 (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 3a70b738b376e52482e63f2eb9cc4d7bb62a9b35
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141619"
---
# <a name="creating-custom-attributes-c"></a>カスタム属性の作成 (C#)
属性クラスを定義することで、独自のカスタム属性を作成できます。属性クラスは、<xref:System.Attribute> の直接的または間接的な派生クラスです。これにより、メタデータの中で属性の定義をすばやく簡単に特定できます。 型にそれを記述したプログラマーの名前でタグを付けるとします。 `Author` というカスタム属性クラスを定義します。  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class AuthorAttribute : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public AuthorAttribute(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 クラス名 `AuthorAttribute` は属性の名前 `Author` であり、サフィックス `Attribute` が付きます。 このクラスは `System.Attribute` から派生しているので、カスタム属性クラスです。 コンストラクターのパラメーターはカスタム属性の位置指定パラメーターです。 この例では、`name` が位置指定パラメーターになります。 パブリックな読み取り/書き込みフィールドまたはプロパティは名前付きパラメーターです。 この場合は、`version` が唯一の名前付きパラメーターです。 `AttributeUsage` 属性を使用して、クラスと `struct` の宣言に対してのみ `Author` 属性を有効にしていることに注意してください。  
  
 この新しい属性の使用方法は次のとおりです。  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` には名前付きパラメーター `AllowMultiple` があります。これを使用すると、カスタム属性が 1 回しか指定できない属性か、または複数回指定できる属性かを設定できます。 次のコード例では、複数回指定できる属性が作成されます。  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 次のコード例では、同じ型の複数の属性が 1 つのクラスに適用されます。  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Reflection>
- [C# プログラミング ガイド](../../index.md)
- [カスタム属性の記述](../../../../standard/attributes/writing-custom-attributes.md)
- [リフレクション (C#)](../reflection.md)
- [属性 (C#)](./index.md)
- [リフレクションを使用した属性へのアクセス (C#)](./accessing-attributes-by-using-reflection.md)
- [AttributeUsage (C#)](../../../language-reference/attributes/general.md)
