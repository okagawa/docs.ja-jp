---
title: プロパティ
description: 'オブジェクトに関連付けられている値を表すメンバーである F # プロパティについて説明します。'
ms.date: 05/16/2016
ms.openlocfilehash: a2a4fbfc88831dcb5cad7a2da701969b2e98b2e3
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740199"
---
# <a name="properties"></a>プロパティ

*プロパティ* は、オブジェクトに関連付けられた値を表すメンバーです。

## <a name="syntax"></a>構文

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>Remarks

プロパティは、オブジェクト指向プログラミングにおける "has a" リレーションシップを表します。これは、オブジェクトインスタンスに関連付けられているデータ、または静的なプロパティの場合は型を表します。

プロパティは、基になる値 (バッキングストアとも呼ばれます) を明示的に指定するかどうか、またはコンパイラがバッキングストアを自動的に生成できるようにするかどうかに応じて、2つの方法で宣言できます。 一般に、プロパティが単純な実装であり、プロパティが値または変数の単純なラッパーである場合は、プロパティの自動的な方法を使用することをお勧めします。 プロパティを明示的に宣言するには、キーワードを使用し `member` ます。 この宣言型の構文の後に、 `get` メソッドとメソッドを指定する構文、およびアクセサーを指定する構文が続き `set` ます。 *accessors* 構文セクションに示されている明示的な構文のさまざまな形式は、読み取り/書き込み、読み取り専用、および書き込み専用のプロパティに使用されます。 読み取り専用プロパティの場合は、メソッドのみを定義します `get` 。書き込み専用プロパティの場合は、メソッドのみを定義し `set` ます。 プロパティにアクセサーとアクセサーの両方がある場合は、 `get` `set` 次のコードに示すように、アクセサーごとに異なる属性とアクセシビリティ修飾子を指定できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

メソッドとメソッドの両方を含む読み取り/書き込みプロパティの場合 `get` `set` 、との順序を逆にする `get` `set` ことができます。 また、に対してのみ表示される構文と、を `get` 組み合わせた構文を使用する代わりに、に対してのみ表示される構文を指定することもでき `set` ます。 これにより、個々の `get` またはメソッドが必要になることがある場合に、コメントを簡単にコメントアウトでき `set` ます。 この組み合わせの構文を使用する代わりに、次のコードを参照してください。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

プロパティのデータを保持するプライベート値は、 *バッキングストア* と呼ばれます。 コンパイラによってバッキングストアが自動的に作成されるようにするには、キーワードを使用して `member val` 自己識別子を省略し、プロパティを初期化する式を指定します。 プロパティが変更可能である場合は、を含め `with get, set` ます。 たとえば、次のクラス型には、自動的に実装される2つのプロパティが含まれています。 `Property1` は読み取り専用で、プライマリコンストラクターに指定された引数に初期化され、空の文字列に初期化される設定可能 `Property2` なプロパティです。

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

自動的に実装されるプロパティは、型の初期化の一部であるため、 `let` 型定義のバインディングやバインドと同様に、他のメンバー定義の前に含める必要があり `do` ます。 自動的に実装されるプロパティを初期化する式は、初期化時にのみ評価され、プロパティがアクセスされるたびには評価されないことに注意してください。 この動作は、明示的に実装されたプロパティの動作とは対照的です。 実際には、これらのプロパティを初期化するコードは、クラスのコンストラクターに追加されます。 この違いを示す次のコードについて考えてみます。

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn $"class1.AutoProperty = %d{class1.AutoProperty}"
printfn $"class1.ExplicitProperty = %d{class1.ExplicitProperty}"
```

**出力**

```console
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

前のコードの出力は、AutoProperty の値が繰り返し呼び出されたときに変更されないことを示しています。一方、ExplicitProperty は、呼び出されるたびに変わります。 これは、明示的なプロパティの getter メソッドと同様に、自動的に実装されるプロパティの式は毎回評価されないことを示しています。

>[!WARNING]
>`System.Data.Entity`自動的に実装されるプロパティの初期化には適していない基底クラスのコンストラクターでカスタム操作を実行する Entity Framework () など、いくつかのライブラリがあります。 そのような場合は、明示的なプロパティを使用してみてください。

プロパティは、クラス、構造体、判別共用体、レコード、インターフェイス、および型拡張のメンバーにすることができ、オブジェクト式で定義することもできます。

属性をプロパティに適用できます。 属性をプロパティに適用するには、プロパティの前に別の行に属性を記述します。 詳細については、「[属性](../attributes.md)」を参照してください。

既定では、プロパティはパブリックです。 アクセシビリティ修飾子は、プロパティにも適用できます。 アクセシビリティ修飾子を適用するには、メソッドとメソッドの両方に適用することを意図している場合は、プロパティの名前の直前に追加します `get` `set` 。 `get` `set` 各アクセサーに異なるアクセシビリティが必要な場合は、キーワードとキーワードの前に追加します。 *アクセシビリティ修飾子* は、、、のいずれかにすることができます `public` `private` `internal` 。 詳しくは、「[アクセス制御](../access-control.md)」をご覧ください。

プロパティの実装は、プロパティがアクセスされるたびに実行されます。

## <a name="static-and-instance-properties"></a>静的プロパティとインスタンスプロパティ

プロパティは、静的プロパティまたはインスタンスプロパティにすることができます。 静的プロパティは、インスタンスなしで呼び出すことができ、個々のオブジェクトではなく、型に関連付けられている値に使用されます。 静的プロパティの場合は、自己識別子を省略します。 インスタンスプロパティには、自己識別子が必要です。

次の静的プロパティ定義は、プロパティのバッキングストアである静的フィールドがあるシナリオに基づいてい `myStaticValue` ます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

プロパティは配列に似ていますが、その場合は *インデックス付きプロパティ* と呼ばれます。 詳細については、「 [インデックス付きプロパティ](indexed-properties.md)」を参照してください。

## <a name="type-annotation-for-properties"></a>プロパティの型の注釈

多くの場合、コンパイラには、バッキングストアの型からプロパティの型を推論するのに十分な情報がありますが、型の注釈を追加することによって型を明示的に設定できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>プロパティセットアクセサーの使用

アクセサーを提供するプロパティを設定する `set` には、演算子を使用し `<-` ます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

出力は **20** です。

## <a name="abstract-properties"></a>抽象プロパティ

プロパティは抽象にすることができます。 メソッドと同様に、は、 `abstract` プロパティに関連付けられた仮想ディスパッチがあることを意味します。 抽象プロパティは、完全に抽象的なものにすることができます。つまり、同じクラスに定義を指定する必要はありません。 そのため、このようなプロパティを含むクラスは抽象クラスです。 また、抽象は、プロパティが仮想であることを示すだけで、その場合は定義が同じクラスに存在する必要があります。 抽象プロパティをプライベートにすることはできません。また、1つのアクセサーが抽象型である場合は、もう一方も abstract である必要があります。 抽象クラスの詳細については、「 [抽象クラス](../abstract-classes.md)」を参照してください。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>こちらもご覧ください

- [メンバー](index.md)
- [メソッド](methods.md)
