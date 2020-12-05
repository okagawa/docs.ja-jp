---
title: 配列
description: 'F # プログラミング言語で配列を作成して使用する方法について説明します。'
ms.date: 08/13/2020
ms.openlocfilehash: 96b0d7eaf10d5afcd9a647681d5c2ef2d2fba335
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739752"
---
# <a name="arrays"></a>配列

配列は、0 から始まる一連のデータ要素の、固定サイズの変更可能なコレクションで、その型はすべて同じです。

## <a name="create-arrays"></a>配列の作成

配列は複数の方法で作成できます。 `[|`次の例に示すように、との間に連続する値をセミコロンで区切って指定すると、小さい配列を作成でき `|]` ます。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

各要素を別々の行に配置することもでき、その場合は、セミコロンの区切り記号を省略できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

配列の要素の型は、使用されるリテラルから推論され、すべて同じである必要があります。 次のコードは、1.0 が浮動小数点数で、2 と 3 は整数であるため、エラーになります。

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

シーケンス式を使用して配列を作成することもできます。 1 から 10 までの整数の 2 乗の配列を作成する例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

すべての要素が 0 に初期化される配列を作成するには、`Array.zeroCreate` を使用します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a>アクセス要素

配列要素には、ドット演算子 ( `.` ) と角かっこ (および) を使用してアクセスでき `[` `]` ます。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

配列のインデックスは0から始まります。

また、スライス表記を使用して配列の要素にアクセスすることもできます。この方法では、配列のサブ範囲を指定できます。 スライス表記の例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

スライス表記を使用するときは、配列の新しいコピーが作成されます。

## <a name="array-types-and-modules"></a>配列の型とモジュール

F# の配列の型はすべて、.NET Framework 型の <xref:System.Array?displayProperty=nameWithType> です。 したがって、F# の配列では、<xref:System.Array?displayProperty=nameWithType> で使用できるすべての機能がサポートされます。

[ `Array` モジュール](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html)は、1次元配列に対する操作をサポートします。 `Array2D`、`Array3D`、`Array4D` の各モジュールには、それぞれ、2 次元、3 次元、4 次元の配列の操作をサポートする関数があります。 4 より大きいランクの配列は、<xref:System.Array?displayProperty=nameWithType> を使用して作成できます。

### <a name="simple-functions"></a>単純な関数

[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) 要素を取得します。 [`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) 配列の長さを示します。 [`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) 要素を指定された値に設定します。 これらの関数の使い方を次のコード例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

出力は次のとおりです。

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>配列を作成する関数

既存の配列を必要とせずに配列を作成できる関数がいくつかあります。 [`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) 要素を含まない新しい配列を作成します。 [`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) 指定されたサイズの配列を作成し、すべての要素を指定された値に設定します。 [`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) 次元と要素を生成する関数を指定して、配列を作成します。 [`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) すべての要素が配列の型の0値に初期化される配列を作成します。 これらの関数の例を次のコードに示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

出力は次のとおりです。

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) 既存の配列からコピーされる要素を格納する新しい配列を作成します。 コピーは簡易コピーです。つまり、要素の型が参照型である場合は、参照だけがコピーされ、基になっているオブジェクトはコピーされません。 これを次のコード例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

このコードによる出力は、次のようになります。

```console
[|Test1; Test2; |]
[|; Test2; |]
```

`Test1` という文字列は、最初の配列にのみ表示されます。これは、`firstArray` の参照が、新しい要素を作成する操作によって上書きされるものの、空の文字列への元の参照は影響を受けず、`secondArray` にまだ存在しているためです。 `Test2` という文字列は、両方の配列で表示されます。これは、`Insert` 型に対する <xref:System.Text.StringBuilder?displayProperty=nameWithType> 操作は基になっている <xref:System.Text.StringBuilder?displayProperty=nameWithType> オブジェクトに影響を与え、このオブジェクトは両方の配列で参照されているためです。

[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) 配列のサブ範囲から新しい配列を生成します。 サブ範囲は、開始インデックスと長さで指定します。 `Array.sub` を使用したコードの例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

出力では、サブ配列が要素 5 から開始し、10 個の要素を含むことが示されています。

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) 2つの既存の配列を組み合わせることによって、新しい配列を作成します。

次のコードは、 **Array. append** を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

このコードによる出力は、次のようになります。

```console
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) 新しい配列に含める配列の要素を選択します。 次のコードで `Array.choose` の例を示します。 配列の要素の型は、オプションの型で返される値の型と一致している必要はありません。 この例では、要素の型は `int` ですが、オプションは多項式関数 `elem*elem - 1` の結果であり、浮動小数点数です。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

このコードによる出力は、次のようになります。

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) 既存の配列の各配列要素に対して指定された関数を実行し、関数によって生成された要素を収集し、それらを新しい配列に結合します。 次のコードで `Array.collect` の例を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

このコードによる出力は、次のようになります。

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) 配列のシーケンスを取得し、それらを1つの配列に結合します。 次のコードで `Array.concat` の例を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

このコードによる出力は、次のようになります。

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) ブール条件関数を受け取り、条件が true である入力配列の要素のみを含む新しい配列を生成します。 次のコードで `Array.filter` の例を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

このコードによる出力は、次のようになります。

```console
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) 既存の配列の順序を逆にして、新しい配列を生成します。 次のコードで `Array.rev` の例を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

このコードによる出力は、次のようになります。

```console
"Hello world!"
```

次の例に示すように、パイプライン演算子 () を使用して配列を変換する配列モジュールの関数を簡単に組み合わせることができ `|>` ます。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

出力は次のようになります。

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>多次元配列

多次元配列を作成できますが、多次元配列リテラルを記述するための構文はありません。 [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html)配列要素のシーケンスのシーケンスから配列を作成するには、演算子を使用します。 シーケンスには、配列リテラルまたはリスト リテラルを使用できます。 たとえば、次のコードでは 2 次元の配列が作成されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

また、関数を使用して [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) 2 次元の配列を初期化することもできます。また、3次元と4次元の配列でも同様の関数を使用できます。 これらの関数は、要素の作成に使用する関数を受け取ります。 関数を指定するのではなく、初期値に設定された要素を含む2次元配列を作成するには、関数を使用します。この関数は、 [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) 最大4次元の配列に対しても使用できます。 次のコード例では、まず、目的の要素を含む複数の配列から成る 1 つの配列を作成し、次に、`Array2D.init` を使用して目的の 2 次元配列を生成する方法を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

配列インデックスとスライス構文は、4 ランクまでの配列に使用できます。 複数の次元でインデックスを指定する場合は、次のコード例に示すように、コンマを使用してインデックスを区切ります。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

2 次元配列の型は `<type>[,]` として書き出され (`int[,]`、`double[,]` など)、3 次元配列の型は `<type>[,,]` として書き出されます。このように、次元が高くなるにつれ、書き出される型が変わります。

1 次元配列で使用できる関数のサブセットのうち、多次元配列でも使用できるのは一部だけです。

### <a name="array-slicing-and-multidimensional-arrays"></a>配列スライスと多次元配列

2次元配列 (マトリックス) では、範囲を指定し、ワイルドカード () 文字を使用して `*` 行または列全体を指定することによって、サブマトリックスを抽出できます。

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

多次元配列を、同じまたは下位の次元のサブに分解することができます。 たとえば、単一の行または列を指定して、行列からベクターを取得できます。

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

このスライス構文は、要素アクセス演算子およびオーバーロードされた `GetSlice` メソッドを実装する型に使用できます。 たとえば、次のコードは、F# 2D 配列をラップし、配列のインデックスのサポートを提供する項目プロパティを実装し、3 つのバージョンの `GetSlice` を実装するマトリックス型を作成します。 マトリックス型のテンプレートとしてこのコードの使用が可能であれば、このセクションで説明するすべてのスライスの操作を使用できます。

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn $"{submatrix}"

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn $"{firstCol}"
```

### <a name="boolean-functions-on-arrays"></a>ブール関数 (配列の)

関数 [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) と [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) テスト要素は、それぞれ1つまたは2つの配列にあります。 これらの関数は、テスト用の関数を受け取り、要素 (または `true` の場合は要素のペア) のうち、条件を満たす要素がある場合は `Array.exists2` を返します。

次のコードは、`Array.exists` と `Array.exists2` の使用方法を示しています。 これらの例では、ただ 1 つの引数 (この場合は関数引数) を適用することで、新しい関数を作成しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

このコードによる出力は、次のようになります。

```console
true
false
false
true
```

同様に、関数は配列をテストして、 [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) すべての要素がブール条件を満たすかどうかを判断します。 このバリエーションは、 [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) 同じ長さの2つの配列の要素を含むブール関数を使用することによって同じことを行います。 これらの関数の使い方を次のコード例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

これらの例の出力は次のようになります。

```console
false
true
true
false
```

### <a name="search-arrays"></a>配列の検索

[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) ブール型の関数を受け取り、その関数が返す最初の要素を返し `true` <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> ます。条件を満たす要素が見つからない場合は、を発生させます。 [`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) はと似てい `Array.find` ますが、要素自体の代わりに要素のインデックスを返す点が異なります。

次のコードでは、`Array.find` と `Array.findIndex` を使用して、完全平方かつ完全立方である値を探しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

出力は次のとおりです。

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) はと似てい `Array.find` ますが、結果がオプションの型で `None` あり、要素が見つからない場合はを返します。 一致する要素が配列内にあるかどうかわからない場合は、`Array.tryFind` ではなく、`Array.find` を使用してください。 同様に、 [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) はと似ていますが、 `Array.findIndex` オプションの型が戻り値である点が異なります。 要素が見つからない場合、オプションは `None` です。

`Array.tryFind` を使用したコードの例を次に示します。 このコードでは、前に示したコードを利用しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

出力は次のとおりです。

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

[`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick)要素を検索するだけでなく、要素を変換する必要がある場合は、を使用します。 この関数の結果は、変換した要素をオプションの値として返した最初の要素になります。該当する要素が見つからない場合は、`None` を返します。

`Array.tryPick` の使用方法を次のコードに示します。 この例では、ラムダ式の代わりに、複数のローカル ヘルパー関数を定義することでコードを簡単にしています。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

出力は次のとおりです。

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a>配列に対して計算を実行する

関数は、 [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) 配列内の各要素の平均を返します。 この関数を使用できるのは、整数による正確な除算がサポートされている要素型だけです。そのため、浮動小数点型では使用できますが、整数型では使用できません。 関数は、 [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) 各要素に対して関数を呼び出した結果の平均を返します。 整数型の配列の場合は、`Array.averageBy` を使用し、この関数で各要素を浮動小数点型に変換して計算することもできます。

[`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max)要素型でサポートされている場合は、またはを使用して、 [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) 要素の最大値または最小値を取得します。 同様に、 [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) とを使用すると、最初に関数を実行して [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) 、比較をサポートする型に変換することができます。

[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) 配列の要素を追加し、 [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) 各要素に対して関数を呼び出し、結果を加算します。

戻り値を格納せずに、配列内の各要素に対して関数を実行するには、を使用し [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) ます。 同じ長さの2つの配列を含む関数の場合は、を使用 [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) します。 関数の結果の配列も保持する必要がある場合 [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) は、またはを使用し [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) ます。これは、一度に2つの配列を操作します。

バリエーションを [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) 使用して、 [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) 要素のインデックスを計算に含めることができます。との場合も同様です [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) 。

、、、、、およびの各関数は、 [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) 配列のすべての要素を含むアルゴリズムを実行します。 同様に、バリエーション [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) とは [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) 2 つの配列に対して計算を実行します。

計算を実行するためのこれらの関数は、 [List モジュール](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)内の同じ名前の関数に対応しています。 使用例については、「 [リスト](lists.md)」を参照してください。

### <a name="modify-arrays"></a>配列の変更

[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) 要素を指定された値に設定します。 [`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) 配列内の要素の範囲を、指定した値に設定します。 `Array.fill` のコード例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

出力は次のとおりです。

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

を使用すると、 [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) ある配列のサブセクションを別の配列にコピーできます。

### <a name="convert-to-and-from-other-types"></a>他の型との間での変換

[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) リストから配列を作成します。 [`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) シーケンスから配列を作成します。 [`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) および [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) は、配列型から他のコレクション型に変換します。

### <a name="sort-arrays"></a>配列の並べ替え

[`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort)ジェネリック比較関数を使用して配列を並べ替えるには、を使用します。 キー [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) と呼ばれる値を生成する関数を指定するために *key* 使用します。この関数は、キーの汎用比較関数を使用して並べ替えます。 [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith)カスタム比較関数を指定する場合は、を使用します。 `Array.sort`、`Array.sortBy`、および `Array.sortWith` は、いずれも、並べ替えた配列を新しい配列として返します。 、、およびのバリエーションにより、 [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) 新しい配列が返される代わりに、 [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) 既存の配列が変更されます。

### <a name="arrays-and-tuples"></a>配列と組

関数とは、 [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) 組のペアの配列を配列のタプルに変換します。逆の場合も同様です。 [`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) とは似ていますが、3つの [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) 要素または3つの配列の組で動作する点が異なります。

## <a name="parallel-computations-on-arrays"></a>配列に対する並列計算

モジュールには、 [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) 配列に対して並列計算を実行する関数が含まれています。 このモジュールは、Version 4 より前の .NET Framework を対象とするアプリケーションでは使用できません。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [F# の型](fsharp-types.md)
