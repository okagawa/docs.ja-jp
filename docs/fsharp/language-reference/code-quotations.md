---
title: コード クォート
description: 'F # コードの引用符について説明します。これは、プログラムで F # コード式を生成して操作できる言語機能です。'
ms.date: 08/13/2020
ms.openlocfilehash: dc37fdbd6cd29e5ee94e5c0186dfe2bfeb666f32
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557195"
---
# <a name="code-quotations"></a>コード引用符

この記事では、 *コードの引用符* について説明します。これは、プログラムによって F # コード式を生成して操作できる言語機能です。 この機能を使用すると、F # コードを表す抽象構文ツリーを生成できます。 次に、アプリケーションのニーズに応じて、抽象構文ツリーを走査して処理できます。 たとえば、ツリーを使用すると、F # コードを生成したり、他の言語でコードを生成したりできます。

## <a name="quoted-expressions"></a>引用符で囲まれた式

*引用符で囲ま* れた式は、コード内の f # 式であり、プログラムの一部としてコンパイルされるのではなく、f # の式を表すオブジェクトにコンパイルされます。 引用符で囲まれた式は、型情報を持つか、型情報のない2つの方法のいずれかでマークできます。 型情報を含める場合は、記号とを使用して、引用符で囲まれた `<@` `@>` 式を区切ります。 型情報が不要な場合は、との記号を使用し `<@@` `@@>` ます。 次のコードは、型指定された型指定のない引用符を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

型情報を含めないと、大きな式ツリーを走査する方が高速になります。 型指定された記号で囲まれた式の結果の型はです `Expr<'T>` 。ここで、型パラメーターには、F # コンパイラの型推論アルゴリズムによって決定される式の型があります。 型情報を含まないコード引用符を使用する場合、引用符で囲まれた式の型は非ジェネリック型の [Expr](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html)になります。 型指定されたクラスで [Raw](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr-1.html#Raw) プロパティを呼び出して、 `Expr` 型指定のないオブジェクトを取得でき `Expr` ます。

クラスでは、 `Expr` 引用符で囲まれた式を使用せずに、プログラムによって F # 式オブジェクトを生成できるようにする静的メソッドがいくつかあります。

コード引用符には完全な式を含める必要があることに注意してください。 たとえば、バインドの場合、バインドされた `let` 名前の定義とバインドを使用する追加の式の両方が必要です。 Verbose 構文では、これはキーワードに続く式です `in` 。 モジュールの最上位レベルでは、これはモジュール内の次の式にすぎませんが、引用符で囲まれている必要があります。

したがって、次の式は無効です。

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

ただし、次の式は有効です。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

F # の引用符を評価するには、 [f # の引用符](https://github.com/fsprojects/FSharp.Quotations.Evaluator)を使用する必要があります。 F # expression オブジェクトの評価と実行のサポートを提供します。

F # の引用符には、型の制約情報も保持します。 次の例を確認してください。

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

関数によって生成される制約 `inline` は、コードに保持されます。 関数の順序によって表さ `negate` れるフォームを評価できるようになりました。

## <a name="expr-type"></a>Expr 型

型のインスタンスは `Expr` F # の式を表します。 ジェネリック型と非ジェネリック型の両方 `Expr` が、F # ライブラリのドキュメントに記載されています。 詳細については、「 [Fsharp.core 名前空間](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations.html) と [引用クラス](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html)」を参照してください。

## <a name="splicing-operators"></a>スプライス演算子

スプライスを使用すると、リテラルコードの引用符を、プログラムまたは別のコード引用符から作成した式と組み合わせることができます。 `%`演算子と演算子を使用すると、 `%%` F # 式オブジェクトをコード引用符に追加できます。 型指定さ `%` れた式オブジェクトを型指定された引用符に挿入するには、演算子を使用します。型指定されていない式オブジェクトを型指定された引用符に挿入するには、演算子を使用し `%%` ます。 どちらの演算子も、単項前置演算子です。 このため `expr` 、が型の型指定されていない式である場合 `Expr` 、次のコードは有効です。

```fsharp
<@@ 1 + %%expr @@>
```

また、 `expr` が型の型指定された引用符である場合 `Expr<int>` 、次のコードが有効です。

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>例

### <a name="description"></a>説明

次の例では、コード引用符を使用して F # コードを式オブジェクトに配置し、式を表す F # コードを出力する方法を示します。 `println` `print` F # expression オブジェクト (型 `Expr` ) をわかりやすい形式で表示する再帰関数を含む関数が定義されています。 [Fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-patternsmodule.html)および[fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html)モジュールには、式オブジェクトの分析に使用できるアクティブなパターンがいくつかあります。 この例には、F # 式に出現する可能性のあるすべてのパターンが含まれているわけではありません。 認識されていないパターンは、ワイルドカードパターン () との一致をトリガーし、メソッドを使用して `_` 表示します。このメソッドを使用すると、 `ToString` `Expr` 一致式に追加するアクティブパターンを知ることができます。

### <a name="code"></a>コード

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>出力

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>例

### <a name="description"></a>説明

また、 [Exprshape モジュール](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html) 内の3つのアクティブパターンを使用して、アクティブなパターンが少数の式ツリーを走査することもできます。 これらのアクティブなパターンは、ツリーを走査するときに、ほとんどのノードの情報をすべて必要としない場合に便利です。 これらのパターンを使用すると、F # の式は、次の3つのパターンのいずれかと一致します。式が `ShapeVar` 変数である場合、 `ShapeLambda` 式がラムダ式である場合、または `ShapeCombination` 式が他のものである場合は。 前のコード例のようにアクティブなパターンを使用して式ツリーを走査する場合は、使用可能な F # 式の型をすべて処理するために、さらに多くのパターンを使用する必要があります。また、コードがより複雑になります。 詳細については、「 [Exprshape. の&#124;&#124;](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html#(%20|ShapeVar|ShapeLambda|ShapeCombination|%20))、「スナップショット」を参照してください。また、このパターンを使用します。

次のコード例は、より複雑なトラバーサルの基礎として使用できます。 このコードでは、関数呼び出しを含む式に対して式ツリーが作成され `add` ます。 特定の [呼び出し](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html#(%20|SpecificCall|_|%20)) のアクティブパターンは、 `add` 式ツリー内のへの呼び出しを検出するために使用されます。 このアクティブパターンは、呼び出しの引数を値に割り当て `exprList` ます。 この場合は、2つしか存在しないため、これらの関数は引数に対して再帰的に呼び出されます。 結果は、 `mul` スプライス演算子 () を使用したへの呼び出しを表すコード引用符に挿入され `%%` ます。 `println`前の例の関数は、結果を表示するために使用されます。

もう一方のアクティブパターン分岐のコードは同じ式ツリーを再生成するだけなので、結果として得られる式の変更はからに変更されるだけです `add` `mul` 。

### <a name="code"></a>コード

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>出力

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
