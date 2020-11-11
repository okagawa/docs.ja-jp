---
title: C# 演算子と式 - C# リファレンス
description: C# 演算子と式、演算子の優先順位、および演算子の結合規則について説明します
ms.date: 08/04/2020
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 9e7ca2087938317f7369043e21fd455dbad7f07b
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439663"
---
# <a name="c-operators-and-expressions-c-reference"></a>C# 演算子と式 (C# リファレンス)

C# には多数の演算子が用意されています。 これらの多くは[組み込み型](../builtin-types/built-in-types.md)によってサポートされており、これらの型の値を使用して基本的な操作を実行できます。 これらの演算子には、次のグループが含まれます。

- [算術演算子](arithmetic-operators.md)では、数値オペランドを使用して算術演算が実行されます
- [比較演算子](comparison-operators.md)では、数値オペランドが比較されます
- [ブール論理演算子](boolean-logical-operators.md)では、[`bool`](../builtin-types/bool.md) オペランドに対して論理演算が実行されます
- [ビットごとおよびシフト演算子](bitwise-and-shift-operators.md)では、整数型のオペランドに対してビットごとまたはシフト演算が実行されます
- [等値演算子](equality-operators.md)では、そのオペランドが等しいかどうかが確認されます

通常は、これらの演算子を[オーバーロード](operator-overloading.md)できます。つまり、ユーザー定義型のオペランドに対して演算子の動作を指定できます。

最も単純な C# 式は、変数のリテラル (たとえば、[整数](../builtin-types/integral-numeric-types.md#integer-literals)と[実数](../builtin-types/floating-point-numeric-types.md#real-literals)の数) と名前です。 演算子を使用すると、これらを複雑な式に組み合わせることができます。 演算子の[優先順位](#operator-precedence)と[結合規則](#operator-associativity)によって、式の中の操作の実行順序が決まります。 かっこを使用すれば、演算子の優先順位と結合規則によって定められた評価の順序を変更することができます。

次のコードでは、式の例が代入の右側にあります。

[!code-csharp[expression examples](snippets/shared/Overview.cs#Expressions)]

通常、式によって結果が生成され、別の式に含めることができます。 [`void`](../builtin-types/void.md) メソッド呼び出しは、結果を生成しない式の例です。 次の例に示すように、これは[ステートメント](../../programming-guide/statements-expressions-operators/statements.md)としてのみ使用できます。

```csharp
Console.WriteLine("Hello, world!");
```

C# に用意されている他の種類の式を次に示します。

- [補間された文字列式](../tokens/interpolated.md)では、書式設定された文字列を作成するための便利な構文が提供されます。

  [!code-csharp-interactive[interpolated string](snippets/shared/Overview.cs#InterpolatedString)]

- [ラムダ式](lambda-expressions.md)を使用すると、匿名関数を作成できます。

  [!code-csharp-interactive[lambda expression](snippets/shared/Overview.cs#Lambda)]

- [クエリ式](../keywords/query-keywords.md)を使用すると、C# でクエリ機能を直接使用できるようになります。

  [!code-csharp-interactive[query expression](snippets/shared/Overview.cs#Query)]

[式本体の定義](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)を使用すると、メソッド、コンストラクター、プロパティ、インデクサー、またはファイナライザーの簡潔な定義を提供できます。

## <a name="operator-precedence"></a>演算子の優先順位

複数の演算子を含む式では、優先順位の高い方の演算子が優先順位の低い方の演算子よりも先に評価されます。 次の例では、乗算は加算より優先順位が高いため、最初に乗算が実行されます。

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

演算子の優先順位によって定められた評価の順序を変更するには、かっこを使用します。

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

次の表は、C# の演算子を優先順位の高い順にまとめたものです。 各行内の演算子の優先順位は同じです。

| 演算子 | カテゴリまたは名前 |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-expression-)、[f(x)](member-access-operators.md#invocation-expression-)、[a&#91;i&#93;](member-access-operators.md#indexer-operator-)、[`x?.y`](member-access-operators.md#null-conditional-operators--and-)、[`x?[y]`](member-access-operators.md#null-conditional-operators--and-)、[x++](arithmetic-operators.md#increment-operator-)、[x--](arithmetic-operators.md#decrement-operator---)、[x!](null-forgiving.md)、[new](new-operator.md)、[typeof](type-testing-and-cast.md#typeof-operator)、[checked](../keywords/checked.md)、[unchecked](../keywords/unchecked.md)、[default](default.md)、[nameof](nameof.md)、[delegate](delegate-operator.md)、[sizeof](sizeof.md)、[stackalloc](stackalloc.md)、[x->y](pointer-related-operators.md#pointer-member-access-operator--) | 1 次式 |
| [+x](arithmetic-operators.md#unary-plus-and-minus-operators)、[-x](arithmetic-operators.md#unary-plus-and-minus-operators)、[\!x](boolean-logical-operators.md#logical-negation-operator-)、[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-)、[++x](arithmetic-operators.md#increment-operator-)、[--x](arithmetic-operators.md#decrement-operator---)、[^x](member-access-operators.md#index-from-end-operator-)、[(T)x](type-testing-and-cast.md#cast-expression)、[await](await.md)、[&x](pointer-related-operators.md#address-of-operator-)、[*x](pointer-related-operators.md#pointer-indirection-operator-)、[true and false](true-false-operators.md) | 単項 |
| [x..y](member-access-operators.md#range-operator-) | 範囲 |
| [switch](switch-expression.md) | `switch` 式 |
| [ある場合](with-expression.md) | `with` 式 |
| [x * y](arithmetic-operators.md#multiplication-operator-)、[x / y](arithmetic-operators.md#division-operator-)、[x % y](arithmetic-operators.md#remainder-operator-) | 乗法|
| [x + y](arithmetic-operators.md#addition-operator-)、[x – y](arithmetic-operators.md#subtraction-operator--) | 加法 |
| [x \<\<  y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | シフト |
| [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-)、[x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x >= y](comparison-operators.md#greater-than-or-equal-operator-)、[is](type-testing-and-cast.md#is-operator)、[as](type-testing-and-cast.md#as-operator) | 関係式と型検査 |
| [x == y](equality-operators.md#equality-operator-), [x != y](equality-operators.md#inequality-operator-) | 等価比較 |
| `x & y` | [ブール演算の論理 AND](boolean-logical-operators.md#logical-and-operator-) または[ビット演算の論理 AND](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [ブール演算の論理 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) または[ビット演算の論理 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [ブール演算の論理 OR](boolean-logical-operators.md#logical-or-operator-) または[ビット演算の論理 OR](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | 条件 AND |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | 条件 OR |
| [x ?? y](null-coalescing-operator.md) | Null 合体演算子 |
| [c ? t : f](conditional-operator.md) | 条件演算子 |
| [x = y](assignment-operator.md)、[x += y](arithmetic-operators.md#compound-assignment)、[x -= y](arithmetic-operators.md#compound-assignment)、[x *= y](arithmetic-operators.md#compound-assignment)、[x /= y](arithmetic-operators.md#compound-assignment)、[x %= y](arithmetic-operators.md#compound-assignment)、[x &= y](boolean-logical-operators.md#compound-assignment)、[x &#124;= y](boolean-logical-operators.md#compound-assignment)、[x ^= y](boolean-logical-operators.md#compound-assignment)、[x <<= y](bitwise-and-shift-operators.md#compound-assignment)、[x >>= y](bitwise-and-shift-operators.md#compound-assignment)、[x ??= y](null-coalescing-operator.md)、[=>](lambda-operator.md) | 代入とラムダ宣言 |

## <a name="operator-associativity"></a>演算子の結合規則

演算子の優先順位が同じ場合は、演算子の結合規則によって、操作の実行順序が決まります。

- *結合規則が左から右* の演算子は、左から右に順番に評価されます。 [代入演算子](assignment-operator.md)と [null 合体演算子](null-coalescing-operator.md)を除き、2 項演算子はすべて左からの結合です。 たとえば、`a + b - c` は `(a + b) - c` と評価されます。
- *結合規則が右から左* の演算子は、右から左に評価されます。 代入演算子、null 合体演算子、および[条件演算子`?:`](conditional-operator.md)は、右からの結合です。 たとえば、`x = y = z` は `x = (y = z)` と評価されます。

演算子の結合規則によって定められた評価の順序を変更するには、かっこを使用します。

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>オペランドの評価

式内のオペランドは、演算子の優先順位と結合規則に関係なく、左から右に評価されます。 次の例では、演算子とオペランドが評価される順序を示しています。

| 正規表現 | 評価の順序 |
| ---------- | ------------------- |
|`a + b`|a、b、+|
|`a + b * c`|a、b、c、*、+|
|`a / b + c * d`|a、b、/、c、d、*、+|
|`a / (b + c) * d`|a、b、c、+、/、d、*|

通常、演算子のオペランドはすべて評価されます。 ただし、一部の演算子では、条件付きでオペランドが評価されます。 つまり、このような演算子では、左端のオペランドの値によって、他の (または、どの) オペランドを評価するかどうかが定義されます。 これらの演算子は、条件付き論理 [AND (`&&`)](boolean-logical-operators.md#conditional-logical-and-operator-) および [OR (`||`)](boolean-logical-operators.md#conditional-logical-or-operator-) 演算子、[null 合体演算子 `??` と `??=`](null-coalescing-operator.md)、[null 条件演算子 `?.` と `?[]`](member-access-operators.md#null-conditional-operators--and-)、および[条件演算子 `?:`](conditional-operator.md) です。 詳細については、演算子ごとの説明を参照してください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。

- [式](~/_csharplang/spec/expressions.md)
- [演算子](~/_csharplang/spec/expressions.md#operators)

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [演算子のオーバーロード](operator-overloading.md)
- [式ツリー](../../programming-guide/concepts/expression-trees/index.md)
