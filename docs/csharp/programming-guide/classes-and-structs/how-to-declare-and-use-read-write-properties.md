---
title: 読み取り/書き込みプロパティを宣言および使用する方法 - C# プログラミング ガイド
description: C# で読み取り/書き込みプロパティを使用する方法について説明します。 このサンプルには、読み取り/書き込みプロパティとなるように、get アクセサーと set アクセサーを持つ 2 つのプロパティが含まれています。
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 75f3b4d6fa8595734cf1310c08281c26c829fd84
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899023"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>読み取り/書き込みプロパティを宣言および使用する方法 (C# プログラミング ガイド)

プロパティは、オブジェクトのデータへの保護されていない、制御されず未確認のアクセスに伴うリスクなしにパブリック データ メンバーの利便性を提供します。 これは *アクセサー* を通じて行われます。アクセサーは、基になるデータ メンバーの値を割り当てたり、取得したりする特殊なメソッドです。 [set](../../language-reference/keywords/set.md) アクセサーはデータ メンバーの割り当てを可能にし、[get](../../language-reference/keywords/get.md) アクセサーはデータ メンバーの値を取得します。  
  
 このサンプルでは、`Name` (string) および `Age` (int) という 2 つのプロパティを持つ `Person` クラスを示します。 両方のプロパティは `get` および `set` アクセサーを提供するため、読み取り/書き込みプロパティと見なされます。  
  
## <a name="example"></a>例  

 [!code-csharp[properties#1](snippets/how-to-declare-and-use-read-write-properties/Program.cs#1)]
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  

 前述の例では、`Name` および `Age` プロパティは[パブリック](../../language-reference/keywords/public.md)であり、`get` および `set` アクセサーの両方が含まれます。 そのため、任意のオブジェクトがこれらのプロパティを読み書きできます。 ただし、アクセサーのいずれかを除外することが望ましい場合もあります。 たとえば、次のように `set` アクセサーを省略すると、プロパティが読み取り専用になります。  
  
 [!code-csharp[properties#2](snippets/how-to-declare-and-use-read-write-properties/Program.cs#2)]
  
 また、一方のアクセサーをパブリックに公開し、もう一方を private または protected にすることもできます。 詳細については、「[アクセサーのアクセシビリティの制限 (C# プログラミング ガイド)](./restricting-accessor-accessibility.md)」を参照してください。  
  
 プロパティを宣言すると、プロパティをクラスのフィールドのように使用できます。 そのため、プロパティ値の取得と設定の両方で、次のように自然な構文を使用できます。  
  
 [!code-csharp[properties#3](snippets/how-to-declare-and-use-read-write-properties/Program.cs#3)]
  
 プロパティの `set` メソッドでは、特殊な `value` 変数を使用できることに注意してください。 この変数には、ユーザーが指定した値が含まれます。たとえば、次のように指定します。  
  
 [!code-csharp[properties#4](snippets/how-to-declare-and-use-read-write-properties/Program.cs#4)]
  
 `Person` オブジェクトの `Age` プロパティの値を増分する場合は、次のような簡潔な構文を使用します。  
  
 [!code-csharp[properties#5](snippets/how-to-declare-and-use-read-write-properties/Program.cs#5)]
  
 `set` メソッドと `get` メソッドがそれぞれ使用されてプロパティがモデル化されている場合、上記と同じ内容のコードは次のようになります。  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 この例では、`ToString` メソッドが次のようにオーバーライドされます。  
  
 [!code-csharp[properties#6](snippets/how-to-declare-and-use-read-write-properties/Program.cs#6)]
  
 プログラムでは `ToString` が明示的に使用されないことに注意してください。 既定では、`WriteLine` 呼び出しによって呼び出されます。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [プロパティ](./properties.md)
- [クラスと構造体](./index.md)
