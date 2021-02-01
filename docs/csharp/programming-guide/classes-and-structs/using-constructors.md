---
title: コンストラクターの使用 - C# プログラミング ガイド
description: この例では、C# で new 演算子を使用してクラスをインスタンス化する方法を示します。 新しいオブジェクトに対してメモリが割り当てられると、単純なコンストラクターが呼び出されます。
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 161c243f16f6705fa8fcf79360f92a74e4d0b27b
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899257"
---
# <a name="using-constructors-c-programming-guide"></a>コンストラクターの使用 (C# プログラミング ガイド)

[クラス](../../language-reference/keywords/class.md)または[構造体](../../language-reference/builtin-types/struct.md)を作成する際には、コンストラクターが呼び出されます。 コンストラクターの名前はクラスまたは構造体と同じで、通常は、このコンストラクターによって、新しいオブジェクトのデータ メンバーが初期化されます。  
  
 次の例では、`Taxi` というクラスが、簡単なコンストラクターを使用して定義された後、 [new](../../language-reference/operators/new-operator.md) 演算子によってインスタンス化されます。 `Taxi` コンストラクターは、新しいオブジェクトに対してメモリが割り当てられるとすぐに、`new` 演算子によって呼び出されます。  
  
 [!code-csharp[TaxiExample#1](snippets/using-constructors/Program.cs#1)]
  
 パラメーターを取らないコンストラクターを "*パラメーターなしのコンストラクター*" と呼びます。 `new` 演算子を使ってオブジェクトをインスタンス化する際に `new` に引数を渡さなかった場合、常にパラメーターなしのコンストラクターが呼び出されます。 詳細については、「[インスタンス コンストラクター](./instance-constructors.md)」を参照してください。  
  
 クラスが[静的](../../language-reference/keywords/static.md)である場合を除き、コンストラクターが存在しないクラスには、クラスをインスタンス化できるように、パブリックなパラメーターなしのコンストラクターが C# コンパイラによって割り当てられます。 詳細については、「[静的クラスと静的クラス メンバー](./static-classes-and-static-class-members.md)」を参照してください。  
  
 次のようにコンストラクターをプライベートにすれば、クラスがインスタンス化されないようにできます。  
  
 [!code-csharp[PrivateConstructor#2](snippets/using-constructors/Program.cs#2)]
  
 詳細については、「[プライベート コンストラクター](./private-constructors.md)」を参照してください。  
  
 [struct](../../language-reference/builtin-types/struct.md) 型のコンストラクターはクラス コンストラクターに似ていますが、`structs` には、明示的なパラメーターなしのコンストラクターを含めることができません。パラメーターなしのコンストラクターは、コンパイラによって自動的に提供されるためです。 このコンストラクターは、`struct` 内の各フィールドを[既定値](../../language-reference/builtin-types/default-values.md)に初期化します。 ただし、このパラメーターなしのコンストラクターは、`struct` が `new` によってインスタンス化される場合にのみ呼び出されます。 たとえば、次のコードでは、<xref:System.Int32> のパラメーターなしのコンストラクターが使用されるため、整数が確実に初期化されます。  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 ただし、次のコードでは `new` が使用されておらず、コードは初期化されていないオブジェクトの使用を試みるため、コンパイラ エラーが発生します。  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 これに対して、`structs` をベースにしたオブジェクト (組み込みのすべての数値型など) は、次の例のように、初期化または代入してから使用できます。  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 このため、値型のパラメーターなしのコンストラクターを呼び出す必要はありません。  
  
 クラスと `structs` のどちらも、パラメーターを受け取るコンストラクターを定義できます。 パラメーターを受け取るコンストラクターは、`new` ステートメントまたは [base](../../language-reference/keywords/base.md) ステートメントを使用して呼び出す必要があります。 クラスと `structs` は複数のコンストラクターを定義することもできます。また、どちらも、パラメーターなしのコンストラクターの定義には必要ありません。 次に例を示します。  
  
 [!code-csharp[EmployeeExample#3](snippets/using-constructors/Program.cs#3)]
  
 このクラスは、次のいずれかのステートメントを使用して作成できます。  
  
 [!code-csharp[InstantiatingEmployeeConstructors#4](snippets/using-constructors/Program.cs#4)]
  
 コンストラクターでは、`base` キーワードを使用して、基底クラスのコンストラクターを呼び出すことができます。 次に例を示します。  
  
 [!code-csharp[ManagerInheritingEmployee#5](snippets/using-constructors/Program.cs#5)]
  
 この例では、コンストラクターのブロックを実行する前に、基底クラスのコンストラクターを呼び出しています。 `base` キーワードは、パラメーターの有無に関係なく使用できます。 コンストラクターのパラメーターは、`base` のパラメーターまたは式の一部として使用できます。 詳細については、「[base](../../language-reference/keywords/base.md)」を参照してください。  
  
 派生クラスで基底クラスのコンストラクターが `base` キーワードを使用して明示的に呼び出されていない場合、パラメーターなしのコンストラクター (存在する場合) は暗黙的に呼び出されます。 つまり、次に示すコンストラクターの宣言は実質的に同じです。  
  
 [!code-csharp[ManagerImplicitlyCallingParameterlessBaseConstructor#6](snippets/using-constructors/Program.cs#6)]
  
 [!code-csharp[ManagerExplicitlyCallingParameterlessBaseConstructor#7](snippets/using-constructors/Program.cs#7)]
  
 基底クラスがパラメーターなしのコンストラクターを提供しない場合、派生クラスでは、`base` を使って基本コンストラクターを明示的に呼び出す必要があります。  
  
 コンストラクターで [this](../../language-reference/keywords/this.md) キーワードを使用すると、同じオブジェクトで別のコンストラクターを呼び出すことができます。 `base` と同様、`this` もパラメーターの有無に関係なく使用でき、コンストラクターのパラメーターはいずれも `this` のパラメーターとしても、式の一部としても使用できます。 たとえば、上の例の 2 番目のコンストラクターは `this` を使用して次のように書き直すことができます。  
  
 [!code-csharp[EmployeeCallingConstructorInSameClass#8](snippets/using-constructors/Program.cs#8)]
  
 上の例で `this` キーワードを使用すると、このコンストラクターが呼び出されます。  
  
 [!code-csharp[ConstructorBeingCalledByThisKeyword#9](snippets/using-constructors/Program.cs#9)]
  
 コンストラクターは、[public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) または [private protected](../../language-reference/keywords/private-protected.md) としてマークできます。 こうしたアクセス修飾子により、クラスのユーザーによるクラスの作成方法が定義されます。 詳細については、「[アクセス修飾子](./access-modifiers.md)」を参照してください。  
  
 コンストラクターは、[static](../../language-reference/keywords/static.md) キーワードを使用して静的として宣言できます。 静的コンストラクターは、静的フィールドがアクセスされる直前に自動的に呼び出され、通常は静的なクラス メンバーを初期化するために使用されます。 詳細については、「[静的コンストラクター](./static-constructors.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  

詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[インスタンス コンストラクター](~/_csharplang/spec/classes.md#instance-constructors)と[静的コンストラクター](~/_csharplang/spec/classes.md#static-constructors)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [クラスと構造体](./index.md)
- [コンストラクター](./constructors.md)
- [ファイナライザー](./destructors.md)
