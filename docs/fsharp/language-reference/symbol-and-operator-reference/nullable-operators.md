---
title: Null 許容の演算子
description: 'F # プログラミング言語で使用できる null 許容型の演算子について説明します。'
ms.date: 05/16/2016
ms.openlocfilehash: 9ac6afc2c3f4277ee6e93b1ccb3d21f892926b4b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740368"
---
# <a name="nullable-operators"></a>Null 許容の演算子

Null 値を許容する演算子は、一方または両方で null 許容型の算術演算を使用する二項演算または比較演算子です。 Null 許容型は、実際の値の代わりに null を許容するデータベースなどのソースからデータを操作するときに頻繁に発生します。 クエリ式では、null 値を許容する演算子が頻繁に使用されます。 算術演算子と比較演算子に加えて、変換演算子を使用して null 許容型間で変換を行うこともできます。 特定のクエリ演算子の null 許容バージョンもあります。

## <a name="table-of-nullable-operators"></a>Null 値を許容する演算子の表

次の表に、F # 言語でサポートされている null 許容の演算子を示します。

|左に null 値を許容|Null 値を許容|両方の側で null 値を許容|
|---|---|---|
|[? >=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E=%20))|[>=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3E=?%20))|[? >=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E=?%20))|
|[>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E%20))|[> ますか?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3E?%20))|[? > ですか?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E?%20))|
|[? <=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C=%20))|[<=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C=?%20))|[? <=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C=?%20))|
|[<](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%20))|[< ますか?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C?%20))|[? < ですか?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C?%20))|
|[?=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?=%20))|[=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20=?%20))|[?=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?=?%20))|
|[<>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%3E%20))|[<> ますか?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C%3E?%20))|[? <> ですか?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%3E?%20))|
|[?+](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?+%20))|[+?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20+?%20))|[?+?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?+?%20))|
|[?-](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?-%20))|[-?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20-?%20))|[?-?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?-?%20))|
|[?*](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?*%20))|[*?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20*?%20))|[?*?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?*?%20))|
|[?/](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?/%20))|[/?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20/?%20))|[?/?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?/?%20))|
|[?%](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%%20))|[%?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%?%20))|[?%?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%?%20))|

## <a name="remarks"></a>注釈

Null 許容型の演算子は、 [nullableoperators.](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html) モジュールの名前空間 [fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq.html)に含まれています。 Null 許容型データの型は `System.Nullable<'T>` です。

クエリ式では、null 許容型は、値ではなく null 値を許容するデータソースからデータを選択するときに発生します。 SQL Server データベースでは、テーブル内の各データ列には、null が許可されるかどうかを示す属性があります。 Null が許容される場合、データベースから返されるデータには、、などのプリミティブデータ型では表現できない null を含めることができ `int` `float` ます。 したがって、データはではなく、として返され `System.Nullable<int>` `int` `System.Nullable<float>` `float` ます。 実際の値は、プロパティを使用してオブジェクトから取得でき `System.Nullable<'T>` `Value` ます。また、メソッドを `System.Nullable<'T>` 呼び出すことによって、オブジェクトに値があるかどうかを判断でき `HasValue` ます。 もう1つの便利な方法として、 `System.Nullable<'T>.GetValueOrDefault` メソッドがあります。このメソッドを使用すると、適切な型の値または既定値を取得できます。 既定値は、0、0.0、またはのような "ゼロ" 値の形式です `false` 。

Null 許容型は、やなどの通常の変換演算子を使用して null 非許容のプリミティブ型に変換でき `int` `float` ます。 Null 許容型に対して変換演算子を使用することにより、1つの null 許容型から別の null 許容型に変換することもできます。 適切な変換演算子の名前は標準の演算子と同じですが、 [fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq.html)名前空間の null 値を[許容](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullablemodule.html)するモジュールという別のモジュールにあります。 通常は、クエリ式を操作するときに、この名前空間を開きます。 その場合は、 `Nullable.` 次のコードに示すように、適切な変換演算子にプレフィックスを追加することによって、null 許容型変換演算子を使用できます。

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn $"%f{float nullableFloat}"
```

出力は `10.000000` になります。

クエリ式で使用するために、などの null 許容型のデータフィールドに対するクエリ演算子 `sumByNullable` も存在します。 Null 非許容型のクエリ演算子は、null 許容型との型との互換性がないため、null 許容型のデータ値を操作する場合は、適切なクエリ演算子の null 許容バージョンを使用する必要があります。 詳細については、「 [クエリ式](../query-expressions.md)」を参照してください。

次の例では、F # クエリ式で null 許容演算子を使用する方法を示します。 最初のクエリは、null 許容演算子を使用せずにクエリを記述する方法を示しています。2番目のクエリは、null 許容の演算子を使用する同等のクエリを示しています。 このサンプルコードを使用するようにデータベースを設定する方法など、完全なコンテキストについては、「 [チュートリアル: 型プロバイダーを使用した SQL Database へのアクセス](../../tutorials/type-providers/index.md)」を参照してください。

```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq

[<Generate>]
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">

let db = dbSchema.GetDataContext()

query {
    for row in db.Table2 do
    where (row.TestData1.HasValue && row.TestData1.Value > 2)
    select row
} |> Seq.iter (fun row -> printfn $"%d{row.TestData1.Value} %s{row.Name}")

query {
    for row in db.Table2 do
    // Use a nullable operator ?>
    where (row.TestData1 ?> 2)
    select row
} |> Seq.iter (fun row -> printfn "%d{row.TestData1.GetValueOrDefault()} %s{row.Name}")
```

## <a name="see-also"></a>こちらもご覧ください

- [型プロバイダー](../../tutorials/type-providers/index.md)
- [クエリ式](../query-expressions.md)
