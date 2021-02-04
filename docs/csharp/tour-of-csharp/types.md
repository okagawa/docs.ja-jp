---
title: 型とそのメンバーの定義 ‐ C# のツアー
description: プログラムの構成要素は型です。 C# でクラス、構造体、インターフェイスなどを作成する方法について説明します。
ms.date: 08/06/2020
ms.openlocfilehash: b1ce24611fec6fdf01d5ecb8d6ae974e147c78c5
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216604"
---
# <a name="types-and-members"></a>型とメンバー

C# は、オブジェクト指向言語として、カプセル化、継承、およびポリモーフィズムの概念をサポートしています。 クラスは 1 つの親クラスから直接継承でき、任意の数のインターフェイスを実装できます。 親クラスの仮想メソッドをオーバーライドする場合、誤って再定義しないように、`override` キーワードを指定する必要があります。 C# の構造体はコンパクトなクラスのようなものです。インターフェイスを実装できるスタック割り当て型ですが、継承はサポートされていません。 C# には、主にデータ値を格納する目的を持つクラス型であるレコードも用意されています。

## <a name="classes-and-objects"></a>クラスとオブジェクト

"*クラス*" は C# の最も基本的な型です。 クラスは、状態 (フィールド) とアクション (メソッドおよびその他の関数メンバー) を 1 つの単位としてまとめたデータ構造です。 クラスには、*オブジェクト* とも呼ばれる、クラスの *インスタンス* の定義があります。 クラスでは、"*継承*"と "*ポリモーフィズム*" をサポートします。これによって "*派生クラス*" が "*基底クラス*" を拡張して特殊化できます。

新しいクラスはクラス宣言を使用して作成されます。 クラス宣言は、ヘッダーで始まります。 ヘッダーでは次を指定します。

- クラスの属性と修飾子
- クラスの名前
- 基底クラス ([基底クラス](#base-classes)から継承する場合)
- このクラスによって実装されるインターフェイス。

ヘッダーの後にはクラス本体が続きます。これは、区切り記号 `{` と `}` の間に記述するメンバー宣言のリストで構成されます。

次のコードは、`Point` という名前の単純なクラスの宣言を示しています。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointClass":::

クラスのインスタンスは `new` 演算子を使用して作成されます。この演算子は新しいインスタンスのメモリを割り当て、コンストラクターを呼び出してインスタンスを初期化し、インスタンスへの参照を返します。 次のステートメントは、2 つの `Point` オブジェクトを作成し、2 つの変数に、それらのオブジェクトへの参照を格納します。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePoints":::

オブジェクトで占有されたメモリは、そのオブジェクトに到達できなくなると自動的に解放されます。 C# では、オブジェクトの割り当てを明示的に解除する必要がなく、また解除することもできません。

### <a name="type-parameters"></a>型パラメーター

ジェネリック クラスでは "[***型パラメーター**](../programming-guide/generics/index.md)" を定義します。 型パラメーターは、山かっこで囲まれた型パラメーターの一連の名前です。 型パラメーターは、クラス名の後にあります。 これで、クラスのメンバーを定義するクラス宣言の本体で型パラメーターを使用できます。 次の例では、`Pair` の型パラメーターは `TFirst` と `TSecond` です。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DefinePairClass":::

型パラメーターを受け取るために宣言されるクラス型は、"ジェネリック クラス型" と呼ばれます。 構造体、インターフェイス、およびデリゲートの型もジェネリックです。
ジェネリック クラスを使用する場合は、それぞれの型パラメーターの型引数を指定する必要があります。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePairObject":::

上記の `Pair<int,string>` のような、型引数が指定されたジェネリック型は "*構築された型*" と呼ばれます。

### <a name="base-classes"></a>基底クラス

クラスの宣言で、基底クラスを指定する場合もあります。 クラス名と型パラメーターの後には、コロンと基底クラスの名前を指定します。 基底クラスの指定の省略は、`object` 型からの派生と同じです。 次の例の `Point3D` の基底クラスは `Point` です。 最初の例の `Point` の基底クラスは `object` です。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="Create3DPoint":::

クラスは、その基底クラスのメンバーを継承します。 継承は、クラスにその基底クラスのほぼすべてのメンバーが暗黙的に含まれることを意味します。 クラスは、インスタンス コンストラクター、静的コンストラクター、およびファイナライザーを継承しません。 派生クラスでは、継承するメンバーに新しいメンバーを追加できますが、継承されたメンバーの定義を削除することはできません。 前述の例では、`Point3D` は、`Point` から `X` メンバーと `Y` メンバーを継承しており、各 `Point3D` インスタンスには、`X`、`Y`、`Z` の 3 つのプロパティが含まれています。

暗黙的な変換は、クラス型からその基底クラス型のいずれかに存在します。 クラス型の変数は、そのクラスのインスタンスまたは任意の派生クラスのインスタンスを参照できます。 たとえば、前述のクラス宣言では、`Point` 型の変数が `Point` または `Point3D` を参照できます。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplicitCastToBase":::

## <a name="structs"></a>構造体

クラスは、継承とポリモーフィズムをサポートする型を定義します。 これにより、派生クラスの階層に基づいて高度なビヘイビアーを作成できます。 これに対し、"[***構造体**](../language-reference/builtin-types/struct.md)" 型は、データ値を格納することを主な目的とするより単純な型です。 構造体では基本データ型を宣言できません。これらは、暗黙的に <xref:System.ValueType?displayProperty=nameWithType> から派生します。 `struct` 型から、他の `struct` 型を派生させることはできません。 これらは、暗黙的にシールされています。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointStruct":::

## <a name="interfaces"></a>インターフェイス

"[_*_インターフェイス_*_](../programming-guide/interfaces/index.md)" では、クラスと構造体によって実装できるコントラクトを定義します。 1 つのインターフェイスには、メソッド、プロパティ、イベント、およびインデクサーが含まれる場合があります。 インターフェイスは、定義するメンバーの実装を通常行いません。インターフェイスを実装するクラスまたは構造体が提供する必要があるメンバーを指定するだけです。

インターフェイスでは "_*_多重継承_*_" を使用できます。 次の例では、インターフェイス `IComboBox` は `ITextBox` と `IListBox` の両方から継承します。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FirstInterfaces":::

クラスと構造体は、複数のインターフェイスを実装できます。 次の例では、クラス `EditBox` は `IControl` と `IDataBound` の両方を実装しています。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplementInterfaces":::

クラスまたは構造体が特定のインターフェイスを実装する場合、そのクラスまたは構造体のインスタンスはそのインターフェイス型に暗黙的に変換できます。 次に例を示します。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UseInterfaces":::

## <a name="enums"></a>列挙型

"[_*_列挙_*_](../language-reference/builtin-types/enum.md)" 型では、一連の定数値を定義します。 次の `enum` では、さまざまな根菜の定数の定義を宣言しています。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="EnumDeclaration":::

`enum` は組み合わせてフラグとして使用できるよう、定義することもできます。 次の宣言では、4 つの季節のフラグのセットを宣言しています。 任意に季節を組み合わせることも、すべての季節を含む `All` 値を含め、適用することも可能です。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FlagsEnumDeclaration":::

次の例では、上記の両列挙型を宣言しています。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UsingEnums":::

## <a name="nullable-types"></a>null 許容型

すべての型の変数は、"_*_null 非許容_*_" または "_*_null 許容_*_" として宣言できます。 null 許容の変数には、値がないことを示す `null` 値をさらに含めることができます。 null 許容値型 (構造体または列挙型) は、<xref:System.Nullable%601?displayProperty=nameWithType> で表します。 null 非許容の参照型と null 許容の参照型はいずれも、基になる参照型によって表します。 この区別は、コンパイラと一部のライブラリに読み取られたメタデータによって表します。 null 許容の参照が、値を最初に `null` に対してチェックせずに逆参照されると、コンパイラによって警告が出されます。 null 非許容の参照が `null` である可能性のある値に割り当てられている場合にも、コンパイラによって警告が出されます。 次の例では、`null` に初期化される "_*_null 許容 int_*_" を宣言しています。 次いで、その値を `5` に設定しています。 同じ概念を、"_*_Null 許容文字列_*_" でも示しています。 詳細については、「[null 許容値型](../language-reference/builtin-types/nullable-value-types.md)」と「[null 許容参照型](../nullable-references.md)」を参照してください。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareNullable":::

## <a name="tuples"></a>タプル

C# では、軽量のデータ構造に複数のデータ要素を簡潔な構文でグループ化できる、"[*_タプル_**](../language-reference/builtin-types/value-tuples.md)" がサポートされます。 タプルは、次の例のように、`(` と `)` の間にメンバーの型と名前を宣言することで、インスタンス化できます。

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareTuples":::

タプルは、次の記事で説明する構成要素を使用しない、複数のメンバーを持つデータ構造の代わりとなります。

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](program-building-blocks.md)
