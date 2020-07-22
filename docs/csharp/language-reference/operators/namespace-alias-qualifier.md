---
title: ':: 演算子 - C# リファレンス'
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 84c418627462f83630fe5072a0b0e2089f6588f6
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507127"
---
# <a name="-operator-c-reference"></a>:: 演算子 (C# リファレンス)

エイリアスが設定された名前空間のメンバーにアクセスするには、名前空間エイリアス修飾子 `::` を使います。 `::` 修飾子は 2 つの識別子の間でのみ使用できます。 左側の識別子には、次のエイリアスのいずれかを指定できます。

- [using エイリアス ディレクティブ](../keywords/using-directive.md)を使って作成された名前空間エイリアス:

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- [extern エイリアス](../keywords/extern-alias.md)。
- `global` エイリアス。これはグローバル名前空間エイリアスです。 グローバル名前空間は、名前付き名前空間内で宣言されていない名前空間と型を含んだ名前空間です。 `global` エイリアスを `::` 修飾子と共に使った場合は、ユーザー定義の名前空間エイリアス `global` が存在していたとしても、常にグローバル名前空間が参照されます。

  次の例では、`global` エイリアスを使って、グローバル名前空間のメンバーである .NET の <xref:System> 名前空間にアクセスします。 `global` エイリアスを使わない場合は、`MyCompany.MyProduct` 名前空間のメンバーであるユーザー定義の `System` 名前空間がアクセスされます。

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }

      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```

  > [!NOTE]
  > `global` キーワードは、`::` 修飾子の左側の識別子に指定した場合にのみ、グローバル名前空間エイリアスとなります。

また、[`.` トークン](member-access-operators.md#member-access-expression-)を使って、エイリアスが設定された名前空間のメンバーにアクセスすることもできます。 ただし、`.` トークンは型のメンバーにアクセスするためにも使用されます。 `::` 修飾子を使う場合、その左側の識別子は、同じ名前を持つ型または名前空間が存在したとしても、常に名前空間エイリアスを参照することが保証されます。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)に関するページの「[名前空間エイリアス修飾子](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers)」セクションをご覧ください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# 演算子](index.md)
- [名前空間の使用](../../programming-guide/namespaces/using-namespaces.md)
