---
title: ref キーワード - C# リファレンス
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 07e1b49605c83908f7b9af25e0cb2599a97257c5
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102074"
---
# <a name="ref-c-reference"></a>ref (C# リファレンス)

`ref` キーワードは、参照渡しで渡される値を示します。 このキーワードは、4 つの異なるコンテキストで使用されます。

- メソッド シグネチャとメソッドの呼び出しで、参照によってメソッドに引数を渡します。 詳細については、「[参照渡しで引数を渡す](#passing-an-argument-by-reference)」を参照してください。
- メソッド シグネチャで、参照渡しで呼び出し元に値を返します。 詳細については、[参照戻り値](#reference-return-values)に関するページを参照してください。
- メンバーの本文で、参照戻り値が、呼び出し元によって変更される参照としてローカルに格納されること、または、通常はローカル変数が参照渡しによって別の値にアクセスすることを示します。 詳細については、「[ref ローカル変数](#ref-locals)」を参照してください。
- `struct` の宣言で、`ref struct` または `readonly ref struct` を宣言します。 詳細については、「[構造体型](../builtin-types/struct.md)」の記事の「[`ref` 構造体](../builtin-types/struct.md#ref-struct)」セクションを参照してください。

## <a name="passing-an-argument-by-reference"></a>参照渡しで引数を渡す

メソッドのパラメーター リストで使用した場合、`ref` キーワードは、引数を値ではなく、参照によって渡すことを示します。 `ref` キーワードは、仮パラメーターを引数 (変数にする必要があります) の別名にします。 つまり、パラメーターに対するすべての操作は引数に対して行われます。 たとえば、呼び出し元がローカル変数の式、または配列要素のアクセス式を渡し、呼び出されたメソッドが ref パラメーターが参照するオブジェクトを置き換える場合、メソッドから戻ったとき、呼び出し元のローカル変数または配列要素では新しいオブジェクトが参照されます。

> [!NOTE]
> 参照渡しの概念と参照型の概念を混同しないでください。 2 つの概念は同じではありません。 メソッドのパラメーターは、値型か参照型かどうかに関係なく、`ref` によって変更できます。 参照渡しで渡される場合、値型はボックス化されません。  

`ref` パラメーターを使用するには、メソッド定義と呼び出し元のメソッドの両方が、次の例に示すように `ref` キーワードを明示的に使用する必要があります。  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

`ref` または `in` パラメーターに渡す引数は、渡す前に初期化する必要があります。 これは、引数を渡す前に明示的に初期化する必要がない [out](out-parameter-modifier.md) パラメーターとは異なります。

クラスのメンバーは、`ref`、`in`、または `out` のみが異なるシグネチャを持つことはできません。 1 つの型の 2 つのメンバー間の唯一の違いが、1 つには `ref` パラメーターが存在し、もう 1 つには `out` または `in` パラメーターが存在することである場合、コンパイラ エラーが発生します。 たとえば、次のコードはコンパイルされません。  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

ただし、次の例に示すように、1 つのメソッドに `ref`、`in` または `out` パラメーターがあり、もう 1 つのメソッドに値パラメーターがある場合、メソッドをオーバーロードすることができます。
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 非表示やオーバーライドなど、シグネチャの一致が必要な他の状況では、`in`、`ref`、`out` はシグネチャの一部であり、互いに一致しません。  
  
 プロパティは変数ではありません。 プロパティはメソッドであり、`ref` パラメーターに渡すことはできません。  
  
 次の種類のメソッドには、`ref`、`in`、`out` キーワードを使用することはできません。  
  
- [async](async.md) 修飾子を使用して定義した Async メソッド。  
- [yield return](yield.md) または `yield break` ステートメントを含む Iterator メソッド。

さらに、[拡張メソッド](../../programming-guide/classes-and-structs/extension-methods.md)には次の制約があります。

- 拡張メソッドの最初の引数では、`out` キーワードを使用できません。
- 拡張メソッドの最初の引数が構造体ではない場合、または構造体として制約されていないジェネリック型である場合、その引数で `ref` キーワードを使用することはできません。
- 最初の引数が構造体である場合を除き、`in` キーワードは使用できません。 ジェネリック型では、構造体として制約されている場合であっても、`in` キーワードを使用することはできません。

## <a name="passing-an-argument-by-reference-an-example"></a>参照渡しで引数を渡す:使用例

前の例は、参照によって値型を渡す例でした。 `ref` キーワードを使用して、参照渡しで参照型を渡すこともできます。 参照型を参照渡しで渡すと、呼び出されたメソッドは、参照パラメーターが呼び出し元で参照するオブジェクトに置換できます。 オブジェクトの格納場所は、参照パラメーターの値としてメソッドに渡されます。 パラメーターの格納場所の値を変更する場合は (新しいオブジェクトをポイント)、呼び出し元が参照する格納場所を変更することもできます。 次の例では、参照型のインスタンスを `ref` パラメーターとして渡します。
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

参照型を値渡しまたは参照渡しで渡す方法の詳細については、「[参照型パラメーターの引き渡し](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md)」を参照してください。
  
## <a name="reference-return-values"></a>参照戻り値

参照戻り値 (または ref 戻り値) は、メソッドから呼び出し元に参照渡しで返される値です。 つまり、呼び出し元はメソッドによって返される値を変更することができ、呼び出し元メソッド内のオブジェクトの状態にその変更が反映されます。

参照戻り値は `ref` キーワードを使用して以下に定義されます。

- メソッド シグネチャ。 たとえば、次のメソッド シグネチャは、`GetCurrentPrice` メソッドが参照渡しで <xref:System.Decimal> 値を返すことを示しています。

```csharp
public ref decimal GetCurrentPrice()
```

- メソッドの `return` ステートメントで返される変数と `return` トークンの間。 次に例を示します。

```csharp
return ref DecimalArray[0];
```

呼び出し元がオブジェクトの状態を変更するには、[ref ローカル変数](#ref-locals)として明示的に定義した変数に参照戻り値を格納する必要があります。

次に、メソッド シグネチャとメソッド本体の両方を示す、より完全な ref 戻り値の例を示します。

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

呼び出されたメソッドによって、戻り値が `ref readonly` として宣言されて参照渡しで値が返されることもあり、返された値が呼び出し元のコードで変更できないように強制されることもあります。 呼び出し元のメソッドでは、ローカルの [ref readonly](#ref-readonly-locals) 変数に値を格納することで、返された値のコピーを回避できます。

例については、「[ref 戻り値と ref ローカル変数の使用例](#a-ref-returns-and-ref-locals-example)」を参照してください。

## <a name="ref-locals"></a>ref ローカル変数

ref ローカル変数は、`return ref` を使用して返された値を参照するために使用します。 ref ローカル変数は、初期化して ref 戻り値以外の値にすることができません。 言い換えると、初期化の右側は参照にする必要があります。 ref ローカル変数の値に変更を加えると、参照渡しの値を返すメソッドのオブジェクトの状態に反映されます。

ref ローカル変数を定義するには、変数宣言の前と、参照渡しで値を返すメソッドの呼び出しの直前に、`ref` キーワードを使用します。

たとえば、次のステートメントは、`GetEstimatedValue` という名前のメソッドによって返される ref ローカル変数を定義しています。

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

同じ方法で、参照渡しの値にアクセスできます。 場合によっては、参照渡しの値へのアクセスによって負荷がかかる可能性があるコピー操作が回避され、パフォーマンスが向上します。 たとえば、次のステートメントは、値の参照に使用される ref ローカル値をどのように定義できるかを示しています。

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

どちらの例も、`ref` キーワードは両方の位置で使用する必要があります。そうしないと、コンパイラ エラー CS8172 "値を使用して参照渡し変数を初期化することはできません" が生成されます。

C#7.3 以降、`foreach` ステートメントの反復変数を ref ローカルまたは ref readonly ローカル変数にすることができます。 詳細については、[foreach ステートメント](foreach-in.md)に関する記事を参照してください。

また、C# 7.3 以降では、[ref 代入演算子](../operators/assignment-operator.md#ref-assignment-operator)を使用して、ref ローカルまたは ref readonly ローカル変数を再割り当てできます。

## <a name="ref-readonly-locals"></a>ref readonly ローカル

ref readonly ローカルは、その署名に `ref readonly` があり、`return ref` を使用するメソッドまたはプロパティにより返される値の参照に使用されます。 `ref readonly` 変数は `ref` ローカル変数のプロパティと `readonly` 変数の組み合わせです。それに割り当てられたストレージのエイリアスであり、変更できません。

## <a name="a-ref-returns-and-ref-locals-example"></a>ref 戻り値と ref ローカル変数の使用例

次の例は、`Title` と `Author` という 2 つの <xref:System.String> フィールドを持つ `Book` クラスを定義しています。 また、`Book` オブジェクトのプライベート配列を含む `BookCollection` クラスも定義しています。 個々のブック オブジェクトは、`GetBookByTitle` メソッドを呼び出すことによって参照渡しで返されます。

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

呼び出し元が `GetBookByTitle` によって返される値を ref ローカル変数として格納する場合、呼び出し元が戻り値に加えた変更が `BookCollection` オブジェクトに反映されます。次の例を参照してください。

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目

- [安全で効率的なコードを記述する](../../write-safe-efficient-code.md)
- [ref 戻り値と ref ローカル変数](../../programming-guide/classes-and-structs/ref-returns.md)
- [ref 条件式](../operators/conditional-operator.md#conditional-ref-expression)
- [パラメーターの引き渡し](../../programming-guide/classes-and-structs/passing-parameters.md)
- [メソッド パラメーター](method-parameters.md)
- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
