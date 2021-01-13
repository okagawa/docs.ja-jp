---
title: C# 7.0 の新機能 - C# ガイド
description: C# 言語のバージョン 7.0 での新機能の概要を説明します。
ms.date: 10/02/2020
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: c238439b0f435e579d932b3b1eb13e9b0061fa5f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678222"
---
# <a name="whats-new-in-c-70-through-c-73"></a>C# 7.0 - C# 7.3 の新機能

C# 7.0 - C# 7.3 では、多くの機能が追加され、C# での開発エクスぺリエンスが段階的に改善されました。 この記事では、新しい言語機能とコンパイラ オプションの概要について説明します。 .NET Framework ベースのアプリケーションでサポートされている最新バージョンである C# 7.3 の動作について説明します。

C# 7.1 で[言語バージョンの選択](../language-reference/configure-language-version.md)の構成要素が追加され、これにより、プロジェクト ファイルでコンパイラ言語バージョンが指定できるようになりました。

C# 7.0 - 7.3 で C# 言語に追加された機能とテーマは次のとおりです。

- [タプルと破棄](#tuples-and-discards)
  - 複数のパブリック フィールドを含む、軽量で名前のない型を作成できます。 コンパイラおよび IDE ツールでは、このような型のセマンティクスが認識されます。
  - 破棄は、割り当てられた値を考慮しない場合に割り当てで使用された、一時的な書き込み専用の値です。 タプルおよびユーザー定義の型を分解する場合や、メソッドを `out` パラメーターを使用して呼び出す場合に特に便利です。
- [パターン一致](#pattern-matching)
  - これらの型のメンバーの任意の型と値に基づいて、分岐ロジックを作成できます。
- [`async` `Main`メソッド](#async-main)
  - アプリケーションのエントリ ポイントに `async` 修飾子を設定できます。
- [ローカル関数](#local-functions)
  - 関数を他の関数の中に入れ子にして、関数のスコープと可視性を制限することができます。
- [式形式のメンバーの追加](#more-expression-bodied-members)
  - 式を使用して作成できるメンバーが増加しました。
- [`throw` 式](#throw-expressions)
  - `throw` がステートメントだったためにこれまで許可されなかったコード コンストラクトで例外をスローできるようになりました。
- [`default` リテラル式](#default-literal-expressions)
  - ターゲットの種類を推論できるとき、既定の値式で既定のリテラル式を使用できます。
- [数値リテラルの構文の改善](#numeric-literal-syntax-improvements)
  - 新しいトークンにより、数値定数の読みやすさが向上します。
- [`out` 変数](#out-variables)
  - `out` の値は、それが使用されるメソッドの引数としてインラインで宣言できます。
- [末尾以外の名前付き引数](#non-trailing-named-arguments)
  - 名前付き引数の後ろに位置引数を続けることができます。
- [`private protected` アクセス修飾子](#private-protected-access-modifier)
  - `private protected` アクセス修飾子によって、同じアセンブリ内の派生クラスのアクセスが有効になります。
- [オーバーロード解決の改善](#improved-overload-candidates)
  - オーバーロードの解決のあいまいさを解決するための新しい規則。
- [安全で効率的なコードを記述するための手法](#enabling-more-efficient-safe-code)
  - 参照セマンティクスを使用したさまざまな値の型の使用を有効にする、構文の機能強化の組み合わせ。

最後に、コンパイラに新しいオプションが追加されました。

- `-refout` と `-refonly`: [参照アセンブリの生成](#reference-assembly-generation)を制御します。
- `-publicsign`: オープン ソース ソフトウェア (OSS) のアセンブリの署名を可能にします。
- `-pathmap`: ソース ディレクトリのマッピングを提供します。

この記事の残りでは、各機能の概要について説明します。 各機能について、背後にある論拠と構文について説明します。 `dotnet try` グローバル ツールを使って、これらの機能をご自身の環境で調べることができます。

1. [dotnet try](https://github.com/dotnet/try/blob/master/README.md#setup) グローバル ツールをインストールします。
1. [dotnet/try-samples](https://github.com/dotnet/try-samples) リポジトリを複製します。
1. 現在のディレクトリを、*try-samples* リポジトリの *csharp7* サブディレクトリに設定します。
1. `dotnet try` を実行します。

## <a name="tuples-and-discards"></a>タプルと破棄

C# には、設計の意図を説明するために使用される、クラスと構造体の豊富な構文が用意されています。 ところが、場合によっては、その豊富な構文を使用するために、余分な作業が必要になることがあります。この場合、メリットはごくわずかです。 複数のデータ要素を含む単純な構造を必要とするメソッドを記述することはよくあります。 このようなシナリオをサポートするために、C# には "*タプル*" が追加されました。 タプルとは、データ メンバーを表す複数のフィールドを含む軽量なデータ構造です。 フィールドは検証されず、独自のメソッドを定義することはできません。 C# のタプル型は、`==` と `!=` をサポートしています。 詳しくは、

> [!NOTE]
> タプルは C# 7.0 より前で使用できましたが、効率的でなく、言語サポートがありませんでした。 これは、タプル要素が `Item1` や `Item2` などとしてのみ参照できることを意味しました。 C# 7.0 では、タプルの言語サポートが導入されたことで、新しい、より効率的なタプル型を使用するフィールドのセマンティック名が有効になります。

各メンバーに値を割り当て、任意でタプルの各メンバーにセマンティック名を付けることでタプルを作成できます。

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

`namedLetters` タプルには、`Alpha` と `Beta` と呼ばれるフィールドが含まれています。 これらの名前は、コンパイル時にのみ存在し、実行時にリフレクションを使用してタプルを検査するときなどには保持されません。

タプルの割り当てでは、代入の右辺でフィールドの名前を指定することもできます。

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

状況によっては、メソッドから返されたタプルのメンバーをばらすことが必要になる場合もあります。  そのためには、タプル内のそれぞれの値に対して別個の変数を宣言します。 このばらす行為は、タプルの *分解* と呼ばれます。

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

.NET でも任意の型に同様の分解を指定することができます。 クラスのメンバーとして `Deconstruct` メソッドを記述します。 その `Deconstruct` メソッドは、抽出する各プロパティ用に一連の `out` 引数を提供します。 次の `Point` クラスを考えてみましょう。このクラスは、`X` 座標と `Y` 座標を抽出するデコンストラクター メソッドを指定しています。

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

`Point` をタプルに割り当てて、個々のフィールドを抽出できます。

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

タプルを何度初期化しても、代入の右項に使用される変数は、タプル要素に使用するものと同じ名前になります。タプル要素の名前は、タプルの初期化に使用される変数から推測できます。

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

この機能の詳細については、[タプルの型](../language-reference/builtin-types/value-tuples.md)に関する記事を参照してください。

`out` パラメーターを使用してタプルを分解したりメソッドを呼び出したりする場合に、使用する予定がなく、考慮にも入れない値の変数の定義を強制されることが多くあります。 C# ではこのシナリオを処理するために *破棄* のサポートを追加しています。 破棄は名前が `_` (アンダースコア (_) 文字) の書き込み専用の変数で、破棄するすべての値をこの 1 つの変数に割り当てることができます。 破棄は未割り当ての変数に似ています。代入ステートメントとは異なり、破棄はコードで使用できません。

次のシナリオでは破棄はサポートされません。

- タプルまたはユーザー定義の型を分解する場合。
- [out](../language-reference/keywords/out-parameter-modifier.md) パラメーターを使用してメソッドを呼び出す場合。
- [is](../language-reference/keywords/is.md) および [switch](../language-reference/keywords/switch.md) ステートメントによるパターン マッチング操作。
- 割り当ての値を破棄として明示的に識別する必要がある場合の、スタンドアロン識別子。

次の例では、ある都市の 2 つの異なる年度のデータを含む 6 つのタプルを戻す `QueryCityDataForYears` メソッドを定義しています。 この例のメソッド呼び出しでは、メソッドによって戻された 2 つの人口の値のみが考慮されているため、タプルの残りの値はタプルの分解時に破棄として扱われます。

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

詳細については、[破棄](../discards.md)に関するページを参照してください。

## <a name="pattern-matching"></a>パターン マッチング

"*パターン マッチング*" は、コード内の制御フローを新しい方法で表現できるようにする一連の機能です。 変数の型、値、またはプロパティの値をテストできます。 これらの手法により、より読みやすいコード フローが作成されます。

パターン マッチングでは、`is` 式と `switch` 式がサポートされています。 どちらの式でも、オブジェクトとそのプロパティを検査して、そのオブジェクトが必要なパターンを満たしているかどうかを判定できます。 パターンに追加の規則を指定するには、`when` キーワードを使用します。

`is` パターン式を使用すると、使い慣れた [`is` 演算子](../language-reference/keywords/is.md#pattern-matching-with-is)を拡張し、その型を超えてオブジェクトを照会したり、1 つの命令で結果を割り当てたりできます。 次のコードでは、変数が `int` であるかどうかが確認されます。int の場合、現在の合計に追加されます。

```csharp
if (input is int count)
    sum += count;
```

先の小さな例では、`is` 式の拡張が示されています。 値の型や参照型に対してテストしたり、正しい型の新しい変数に成功した結果を割り当てたりできます。

switch 一致式には、既に C# 言語に含まれている `switch` ステートメントに基づいた、使い慣れた構文があります。 更新された switch 式には新しいコンストラクトがいくつか含まれます。

- `switch` 式を制御する型は、整数型、`Enum` 型、`string`、あるいはそれらの型のいずれかに対応する null 許容型に制限されなくなります。 任意の型を使用できます。
- 各 `case` ラベルで `switch` 式の型をテストできます。 `is` 式と同様に、その型に新しい変数を割り当てることができます。
- `when` 句を追加し、その変数で条件をさらにテストできます。
- `case` ラベルの順序が重要になります。 一致する最初の分岐が実行されます。他の分岐はスキップされます。

次のコードでこれらの新しい機能を確認できます。

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- `case 0:` はおなじみの定数パターンです。
- `case IEnumerable<int> childSequence:` は型パターンです。
- `case int n when n > 0:` は `when` 条件が追加された型パターンです。
- `case null:` は null パターンです。
- `default:` はおなじみの既定ケースです。

C#7.1 以降では、`is` 型パターンと `switch` 型パターンのパターン式は、ジェネリック型パラメーターの型を持つことができます。 これは `struct` 型か `class` 型のいずれかである可能性がある型を確認し、ボックス化を回避するときに最も役立ちます。

パターン マッチングの詳細については、[C# のパターン マッチング](../pattern-matching.md)を参照してください。

## <a name="async-main"></a>async main

*async main* メソッドにより、`Main` メソッドで `await` を使用できます。 以前は次のように記述する必要がありました。

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

それが次のように記述できるようになりました。

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

プログラムによって終了コードが返されない場合、<xref:System.Threading.Tasks.Task> を返す `Main` メソッドを宣言できます。

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

プログラミング ガイドの [async main](../programming-guide/main-and-command-args/index.md) の記事に詳細があります。

## <a name="local-functions"></a>ローカル関数

クラスの多くの設計には、1 つの場所からのみ呼び出されるメソッドが含まれます。 このような追加のプライベート メソッドを使用することで、各メソッドのサイズを小さくし、その焦点を絞ることができます。 *ローカル関数* を使用すると、別のメソッドのコンテキスト内でメソッドを宣言することができます。 ローカル関数のおかげで、クラスを読み取る際に、ローカル メソッドはそれ自体が宣言されているコンテキストからしか呼び出されないことが、簡単にわかります。

ローカル関数には、パブリック反復子メソッドとパブリック非同期メソッドという 2 つの一般的なユース ケースがあります。 どちらの種類のメソッドも、プログラマーが期待するよりも遅くエラーを報告するコードを生成します。 反復子メソッドの場合、例外が検出されるのは、返されたシーケンスを列挙するコードを呼び出した場合のみです。 非同期メソッドの場合、例外が検出されるのは、返された `Task` が待機状態になったときのみです。 次の例では、ローカル関数を使用し、反復子の実装からパラメーター検証を分ける動作を確認できます。

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

同じ手法を `async` メソッドで使用すると、引数の検証で発生する例外が非同期操作の開始前にスローされることを保証できます。

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

次の構文がサポートされるようになりました。

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

属性 `SomeThingAboutFieldAttribute` は、`SomeProperty` のコンパイラによって生成されるバッキング フィールドに適用されます。 詳しくは、C# プログラミング ガイドの「[属性](../programming-guide/concepts/attributes/index.md)」を参照してください。

> [!NOTE]
> ローカル関数によってサポートされる設計の中には、"*ラムダ式*" を使用して実現できるものもあります。 詳細については、[ローカル関数とラムダ式](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)に関するページをご覧ください。

## <a name="more-expression-bodied-members"></a>式形式のメンバーの追加

C# 6 では、メンバー関数の式形式のメンバーと読み取り専用プロパティが導入されました。 C# 7.0 では、式として実装できる許可されたメンバーが拡張されます。 C# 7.0 では、"*コンストラクター*"、"*ファイナライザー*"、`get` アクセサー、および `set` アクセサーを "*プロパティ*" と "*インデクサー*" に実装できます。 それぞれの例を次のコードに示します。

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> この例ではファイナライザーは必要ありませんが、その構文を紹介するために示しています。 アンマネージ リソースを解放する必要がない限り、クラスにファイナライザーを実装しないでください。 また、アンマネージ リソースを直接管理する代わりに、<xref:System.Runtime.InteropServices.SafeHandle> クラスの使用を検討する必要もあります。

式形式のメンバー用のこれらの新しい場所は、C# 言語の重要なマイルストーンです。これらの機能は、オープン ソースの [Roslyn](https://github.com/dotnet/Roslyn) プロジェクトに関わるコミュニティ メンバーによって実装されました。

メソッドを式のようなメンバーに変更することは、[バイナリ互換性がある変更](version-update-considerations.md#binary-compatible-changes)です。

## <a name="throw-expressions"></a>throw 式

C# では、`throw` は常にステートメントでした。 `throw` は式ではなくステートメントであるため、使用できない C# コンストラクトがありました。 これには、条件式、null 結合式、および一部のラムダ式が含まれます。 式形式のメンバーが追加されたことにより、さらに多くの場所で `throw` 式が役に立つようになりました。 C# 7.0 では、このようなコンストラクトを記述できるように、[*throw 式*](../language-reference/keywords/throw.md#the-throw-expression)が導入されています。

この導入により、式ベースのコードをたくさん記述することが簡単になります。 エラー チェックのためにステートメントを追加する必要はありません。

## <a name="default-literal-expressions"></a>既定のリテラル式

既定のリテラル式は既定の値式の拡張版です。 これらの式によって変数が初期化され、既定値になります。 以前は次のように記述していました。

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

それが今では、初期化の右項で種類を省略できるようになりました。

```csharp
Func<string, bool> whereClause = default;
```

詳しくは、「[default 演算子](../language-reference/operators/default.md)」記事の「[default リテラル](../language-reference/operators/default.md#default-literal)」セクションをご覧ください。

## <a name="numeric-literal-syntax-improvements"></a>数値リテラルの構文の改善

数値定数を読み間違えると、コードを初めて読むときにコードを理解するのが難しくなる場合があります。 ビット マスクやその他の記号を用いた値では誤解を招きやすくなります。 C# 7.0 では、使用目的に応じて最も読みやすい形式で数値を記述しできるように、*バイナリ リテラル* と *桁区切り文字* という 2 つの新機能が導入されました。

ビット マスクを作成しているときや、数値をバイナリで表現するとコードが最も読みやすくなる場合は、数字をバイナリで記述します。

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

定数の先頭にある `0b` は、数値が 2 進数として記述されていることを示します。 2 進数は長くなる可能性があるため、前の例の 2 進定数に示されているように、`_` を桁区切り文字として導入すると、ビット パターンが見やすくなることがよくあります。 桁区切り記号は定数のどこにでも置くことができます。 10 進数の場合は、3 桁の区切り記号として使用するのが一般的です。 16 進と 2 進の数値リテラルの先頭に `_` を使用できます。

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

桁区切り記号は、`decimal` 型、`float` 型、`double` 型でも使用できます。

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

これらをまとめると、数値定数をさらに見やすい状態で宣言できます。

## <a name="out-variables"></a>`out` 変数

`out` パラメーターをサポートする既存の構文は、C# 7 で改良されました。 現在は、別の宣言ステートメントを記述するのではなく、メソッド呼び出しの引数リストで `out` 変数を宣言できるようになりました。

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

前の例に示されているように、わかりやすくするために `out` 変数の型を指定することができます。 ただし、この言語では、次のように暗黙的に型指定されたローカル変数を使用できます。

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- コードが読みやすくなる。
  - out 変数は、前のコード行ではなく、使用する場所で宣言します。
- 初期値を割り当てる必要がない。
  - `out` 変数は、メソッド呼び出し内の使用場所で宣言することにより、割り当てる前に誤って使用することがなくなります。

`out` 変数の宣言を許可するために C# 7.0 に追加された構文が、フィールド初期化子、プロパティ初期化子、コンストラクター初期化子、およびクエリ句を含めるように拡張されました。 これにより、次の例に示すようなコードを使用できるようになります。

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

## <a name="non-trailing-named-arguments"></a>末尾以外の名前付き引数

メソッド呼び出しで、位置引数の前に名前付き引数を使用できるようになりました。ただし、そのような名前付き引数が正しい位置にある場合です。 詳細については、「[名前付き引数と省略可能な引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)」を参照してください。

## <a name="private-protected-access-modifier"></a>*private protected* アクセス修飾子

新しい複合アクセス修飾子: `private protected` は、同じアセンブリで宣言されているクラスまたは派生クラスを含むことでメンバーにアクセスできることを示しています。 `protected internal` は同じアセンブリの派生クラスまたはクラスによるアクセスを許可していますが、`private protected` は同じアセンブリで宣言された派生型へのアクセスを制限しています。

詳細については、言語リファレンスの[アクセス修飾子](../language-reference/keywords/access-modifiers.md)に関するページを参照してください。

## <a name="improved-overload-candidates"></a>オーバーロード候補の改善

すべてのリリースにおいて、あいまいなメソッド呼び出しに対する "明らかな" 選択肢が存在する状況に対応するようにオーバーロードの解決ルールが更新されました。 このリリースでは、コンパイラが明らかな選択肢を選択できるようにする 3 つの新しいルールが追加されています。

1. インスタンス メンバーと静的メンバーの両方がメソッド グループに含まれている場合は、インスタンス レシーバーまたはコンテキストを指定せずにメソッドが呼び出されると、コンパイラがインスタンス メンバーを破棄します。 インスタンス レシーバーを使用してメソッドが呼び出された場合、コンパイラは静的メンバーを破棄します。 レシーバーがない場合、コンパイラは静的メンバーだけを静的コンテキストに含めます。それ以外の場合は、静的メンバーとインスタンス メンバーの両方を含めます。 レシーバーがあいまいなインスタンスまたは型である場合、コンパイラは両方のメンバーを含めます。 暗黙的な `this` インスタンス レシーバーを使用できない静的コンテキストには、`this` が定義されないメンバー (静的メンバーなど) の本体および `this` を使用できない場所 (フィールド初期化子やコンストラクター初期化子など) が含まれます。
1. 型引数が制約を満たしていない複数のジェネリック メソッドがメソッド グループに含まれている場合、そのグループのメンバーは候補セットから削除されます。
1. メソッド グループの変換では、戻り値の型がデリゲートの戻り値の型と一致しない候補メソッドが候補セットから削除されます。

適切なメソッドがわかっている場合には、あいまいなメソッドのオーバーロードに対するコンパイラ エラーが少なくなることを認識できるため、この変更点にのみ注意してください。

## <a name="enabling-more-efficient-safe-code"></a>セーフ コードをより効率的にする

アンセーフ コードと同様のパフォーマンスを確保した C# コードを安全に記述できるようにする必要があります。 セーフ コードは、バッファー オーバーラン、ストレイ ポインター、その他のメモリ アクセス エラーなどのエラーを回避します。 ここで説明する新機能は、検証可能なセーフ コードの機能を拡張します。 安全なコンストラクトを使用してより多くのコードを記述するようにしてください。 以下に示す機能によって、コードの記述が容易になります。

次の新機能は、セーフ コードのパフォーマンス向上のテーマをサポートします。

- ピン留めを使用せずに fixed フィールドにアクセスできます。
- `ref` ローカル変数を再割り当てできます。
- `stackalloc` 配列で初期化子を使用できます。
- パターンをサポートする型と共に `fixed` ステートメントを使用できます。
- 追加のジェネリック制約を使用できます。
- パラメーターの `in` 修飾子。引数が参照によって渡されるが、呼び出されたメソッドでは変更されないことを指定します。 引数に `in` 修飾子を加えることは、[ソース互換性がある変更](version-update-considerations.md#source-compatible-changes)です。
- メソッド戻りの `ref readonly` 修飾子。メソッドが参照によってその値を戻しますが、そのオブジェクトに対する書き込みを許可しないことを指定します。 戻り値が値に割り当てられている場合、`ref readonly` 修飾子を追加することは、[ソース互換性がある変更](version-update-considerations.md#source-compatible-changes)です。 既存の `ref` return ステートメントに `readonly` 修飾子を追加することは、[互換性がない変更](version-update-considerations.md#incompatible-changes)です。 呼び出し元は、`readonly` 修飾子を含むように `ref` ローカル変数の宣言を更新する必要があります。
- `readonly struct` 宣言。変更不可の構造体で、そのメンバー メソッドの `in` パラメーターとして渡す必要があることを示します。 既存の構造体の宣言に `readonly` 修飾子を追加することは、[バイナリ互換性がある変更](version-update-considerations.md#binary-compatible-changes)です。
- `ref struct` 宣言。構造体型がマネージド メモリに直接アクセスし、常にスタック割り当てが必要であることを示します。 既存の `struct` の宣言に `ref` 修飾子を追加することは、[互換性がない変更](version-update-considerations.md#incompatible-changes)です。 `ref struct` をクラスのメンバーにすることはできません。また、ヒープ上に割り当てられている可能性がある他の場所で使用することもできません。

これらすべての変更点の詳細については、[安全で効率的なコードを記述する方法](../write-safe-efficient-code.md)に関するページを参照してください。

### <a name="ref-locals-and-returns"></a>ref ローカル変数と戻り値

この機能により、他の場所に定義されている変数への参照を使用したり返したりするアルゴリズムが実現します。 1 つの例として、大規模なマトリックスを使用していて、特定の特性を持つ 1 つの場所を探します。 次のメソッドでは、マトリックスのそのストレージに **参照** が返されます。

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

戻り値を `ref` として宣言し、次のコードのように、マトリックスでその値を変更できます。

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# 言語には、`ref` ローカル変数と戻り値の誤用を防ぐ規則がいくつかあります。

- メソッド シグネチャと、メソッド内のすべての `return` ステートメントに `ref` キーワードを追加する必要があります。
  - それにより、メソッド全体でメソッドは参照渡しで返すことになります。
- `ref return` は値の変数か `ref` 変数に割り当てることができます。
  - 呼び出し元により、戻り値がコピーされるかどうかが制御されます。 戻り値を割り当てるとき、`ref` 修飾子を省略すると、呼び出し元はストレージの参照ではなく、値のコピーを求めることになります。
- 標準的なメソッドの戻り値を `ref` ローカル変数に割り当てることはできません。
  - したがって、`ref int i = sequence.Count();` のようなステートメントは使用できません。
- 有効期間がメソッドの実行期間を超えない変数に `ref` を返すことはできません。
  - つまり、ローカル変数または類似のスコープの変数への参照を返すことはできません。
- `ref` ローカル変数と戻り値は、非同期メソッドと共に使用することはできません。
  - コンパイラは、非同期メソッドが戻るときに、参照先の変数が、最終的な値に設定されているかどうかを認識できません。

ref ローカル変数および ref 戻り値の追加により、値のコピーを回避したり、逆参照操作を複数回実行したりすることで、より効率的なアルゴリズムを実現できます。

戻り値に `ref` を追加することは、[ソース互換性がある変更](version-update-considerations.md#source-compatible-changes)です。 既存のコードはコンパイルされますが、参照戻り値は割り当て時にコピーされます。 呼び出し元は、戻り値を参照として格納するために、戻り値の記憶域を `ref` ローカル変数に更新する必要があります。

初期化後に別のインスタンスを参照するために、`ref` ローカル変数を再割り当てできるようになりました。 次のコードがコンパイルされます。

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

詳しくは、[`ref` 戻り値と `ref` ローカル変数](../programming-guide/classes-and-structs/ref-returns.md)に関する記事と [`foreach`](../language-reference/keywords/foreach-in.md) に関する記事を参照してください。

詳しくは、[ref](../language-reference/keywords/ref.md) キーワードに関する記事をご覧ください。

### <a name="conditional-ref-expressions"></a>条件付きの `ref` 式

最後に、条件式で値の結果ではなく参照結果を生成することができます。 たとえば、次のように記述して、2 つの配列のいずれかに含まれる最初の要素の参照を取得できます

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

変数 `r` は、`arr` または `otherArr` の最初の値の参照です。

詳細については、言語リファレンスの[条件演算子 (?:)](../language-reference/operators/conditional-operator.md) に関するページを参照してください。

### <a name="in-parameter-modifier"></a>`in` パラメーター修飾子

`in` キーワードは、ref と out の既存のキーワードを補完し、引数を参照で渡します。 `in` キーワードでは、引数を参照で渡すことが指定されますが、呼び出されたメソッドでは値は変更されません。

次のコードに示すように、値または読み取り専用参照によって渡されるオーバーロードを宣言できます。

```csharp
static void M(S arg);
static void M(in S arg);
```

値によるオーバーロード (前述の例の 1 番目) の方が、読み取り専用参照による方法よりも優れています。 readonly 参照引数を使用してバージョンを呼び出すには、メソッドの呼び出し時に `in` 修飾子を含める必要があります。

詳しくは、[`in` パラメーター修飾子](../language-reference/keywords/in-parameter-modifier.md)に関する記事を参照してください。

### <a name="more-types-support-the-fixed-statement"></a>`fixed` ステートメントをサポートする型の増加

`fixed` ステートメントは、限られた一連の型をサポートしていました。 C# 7.3 以降では、`ref T` または `ref readonly T` を返す `GetPinnableReference()` メソッドを格納する型として `fixed` を使用できます。 この機能の追加により、`fixed` を <xref:System.Span%601?displayProperty=nameWithType> および関連する型と共に使用できます。

詳しくは、言語リファレンスの [`fixed` ステートメント](../language-reference/keywords/fixed-statement.md)に関する記事を参照してください。

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>ピン留めが不要な `fixed` フィールドのインデックス付け

たとえば、次の構造体があるとします。

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

以前のバージョンの C# では、`myFixedField` の一部であるいずれかの整数にアクセスするために変数のピン留めが必要でした。 今では、次のコードは、変数 `p` を別の `fixed` ステートメントの内部にピン留めせずに、コンパイルされます。

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

変数 `p` は `myFixedField` の 1 個の要素にアクセスします。 個別の `int*` 変数を宣言する必要はありません。 `unsafe` コンテキストは引き続き必要です。 以前のバージョンの C# では、2 番目の固定ポインターを宣言する必要があります。

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

詳細については、[`fixed` ステートメント](../language-reference/keywords/fixed-statement.md)に関する記事を参照してください。

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` 配列による初期化子のサポート

配列を初期化する際に、配列内の要素の値を指定することが可能でした。

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

現在では、`stackalloc` で宣言された配列に同じ構文を適用できます。

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

詳細については、「[`stackalloc` 演算子](../language-reference/operators/stackalloc.md)」の記事を参照してください。

### <a name="enhanced-generic-constraints"></a>ジェネリック制約の拡張

型パラメーターの基底クラスの制約として、<xref:System.Enum?displayProperty=nameWithType> 型または <xref:System.Delegate?displayProperty=nameWithType> 型を指定できるようになりました。

また、新しい `unmanaged` 制約を使用して、型パラメーターが null 非許容で[アンマネージ型](../language-reference/builtin-types/unmanaged-types.md)である必要があることを指定することもできます。

詳しくは、[`where` ジェネリック制約](../language-reference/keywords/where-generic-type-constraint.md)および[型パラメーターの制約](../programming-guide/generics/constraints-on-type-parameters.md)に関する記事を参照してください。

これらの制約を既存の型に追加することは、[互換性のない変更](version-update-considerations.md#incompatible-changes)です。 クローズ ジェネリック型は、これらの新しい制約を満たさなくなります。

### <a name="generalized-async-return-types"></a>一般化された async の戻り値の型

非同期メソッドから `Task` オブジェクトを返すと、特定のパスでパフォーマンスのボトルネックが発生する可能性があります。 `Task` は参照型です。したがって、これを使うことは、オブジェクトを割り当てることを意味します。 `async` 修飾子で宣言されたメソッドがキャッシュされた結果を返すか、同期的に完了する場合、追加の割り当ては、コードのパフォーマンスが重要なセクションにおいて大きな時間コストにつながります。 厳密なループ処理でこのような割り当てが発生した場合、コストがかかる場合があります。

新しい言語機能では、非同期メソッドの戻り値の型が `Task`、`Task<T>`、`void` に限定されません。 返される型は引き続き非同期パターンを満たす必要があります。つまり、`GetAwaiter` メソッドはアクセス可能である必要があります。 1 つの具体的な例として、この新しい言語機能を使用するために .NET に `ValueTask` 型が追加されました。

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> <xref:System.Threading.Tasks.ValueTask%601> 型を使用するには、NuGet パッケージ [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) > を追加する必要があります。

この機能強化は、ライブラリの作成時、パフォーマンス クリティカルなコードに `Task` を割り当てることを回避する目的で非常に便利です。

## <a name="new-compiler-options"></a>新しいコンパイラ オプション

新しいコンパイラ オプションでは、C# プログラムの新しいビルドと DevOps のシナリオがサポートされます。

### <a name="reference-assembly-generation"></a>参照アセンブリ生成

"*参照専用アセンブリ*" を生成する新しい 2 つのコンパイラ オプション [-refout](../language-reference/compiler-options/refout-compiler-option.md) と [-refonly](../language-reference/compiler-options/refonly-compiler-option.md) があります。
リンク先の記事には、オプションと参照アセンブリに関する詳細があります。

### <a name="public-or-open-source-signing"></a>公開署名またはオープン ソース署名

`-publicsign` コンパイラ オプションは、公開キーを使用してアセンブリに署名するようにコンパイラに指示します。 アセンブリは署名済みとしてマークされますが、署名は公開キーから取得されます。 このオプションでは、公開キーを使用するオープン ソース プロジェクトから署名済みのアセンブリをビルドできます。

詳しくは、[-publicsign コンパイラ オプション](../language-reference/compiler-options/publicsign-compiler-option.md)の記事を参照してください。

### <a name="pathmap"></a>pathmap

`-pathmap` コンパイラ オプションは、ビルド環境からのソース パスをマップ済みのソース パスに置き換えるようにコンパイラに指示します。 `-pathmap` オプションは、コンパイラが記述した PDB ファイルまたは <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> のソース パスを制御します。

詳しくは、[-pathmap コンパイラ オプション](../language-reference/compiler-options/pathmap-compiler-option.md)の記事を参照してください。
