---
title: XML ファイルの処理 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 1e3d96f9398f2c08ed715111f01987e2d1948439
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287260"
---
# <a name="process-the-xml-file-c-programming-guide"></a>XML ファイルの処理 (C# プログラミング ガイド)

コンパイラは、ドキュメントを生成するためにタグ付けされたコードのコンストラクトごとに、ID 文字列を生成します。 (コードをタグ付けする方法については、[ドキュメント コメント用の推奨タグ](./recommended-tags-for-documentation-comments.md)に関するページを参照してください。)ID 文字列によって、コンストラクトは一意に識別されます。 XML ファイルを処理するプログラムは、ID 文字列を使用して、対応する .NET のメタデータまたはドキュメントを適用するリフレクション項目を識別できます。

## <a name="id-strings"></a>ID 文字列

.xml ファイルは、コードの階層表現ではなく、 要素ごとに生成された ID を持つフラット リストです。

コンパイラは、次の規則に基づいて ID 文字列を生成します。

- 文字列に空白文字は含まれません。

- この文字列の最初の部分は、単一の文字とそれに続くコロンで識別されるメンバーの種類を示します。 使用されるメンバー型は次のとおりです。

    |文字|メンバーの型|メモ|
    |---------------|-----------------|-|
    |N|名前空間|ドキュメント コメントを名前空間に追加することはできませんが、名前空間への cref 参照を行うことはできます (サポートされている場合)。|
    |T|型|クラス、インターフェイス、構造体、列挙型、またはデリゲートの型です。|
    |F|フィールド|
    |P|property|インデクサーまたはその他のインデックス付きプロパティが含まれます。|
    |M|メソッド|コンストラクターや演算子などの特殊なメソッドが含まれます。|
    |E|イベント|
    |!|エラー文字列|あとに続く文字列で、エラーの情報を示します。 C# コンパイラは、解決できないリンクのエラー情報を生成します。|

- 文字列の 2 番目の部分は、項目の完全修飾名で、名前空間のルートから始まります。 項目の名前、それを囲む型、名前空間は、ピリオドで区切られます。 項目の名前自体にピリオドがある場合、名前のピリオドはハッシュ記号 ('#') に置き換えられます。 項目の名前には、ハッシュ記号がないことが前提です。 たとえば、String コンストラクターの完全修飾名は "System.String.#ctor" です。

- プロパティおよびメソッドについては、パラメーターのリストをかっこで囲み、プロパティとメソッドに続けて指定します。 パラメーターがない場合、かっこはありません。 パラメーターはコンマで区切ります。 各パラメーターのエンコードは、.NET のシグネチャでのエンコード方法にそのまま従います。

  - 基本データ型。 通常の型 (ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE) は、型の完全修飾名で表されます。

  - (ELEMENT_TYPE_I4、ELEMENT_TYPE_OBJECT、ELEMENT_TYPE_STRING、ELEMENT_TYPE_TYPEDBYREF、および ELEMENT_TYPE_VOID などの) 組み込み型は、対応する完全な型の完全修飾名で表されます。 たとえば、System.Int32 や System.TypedReference です。

  - ELEMENT_TYPE_PTR は、修飾される型に続けて '\*' と表されます。

  - ELEMENT_TYPE_BYREF は、修飾される型に続けて '\@' と表されます。

  - ELEMENT_TYPE_PINNED は、修飾される型に続けて '^' と表されます。 これは C# コンパイラでは生成されません。

  - ELEMENT_TYPE_CMOD_REQ は、修飾される型に続けて "&#124;" と修飾子クラスの完全修飾名で表されます。 これは C# コンパイラでは生成されません。

  - ELEMENT_TYPE_CMOD_OPT は、修飾される型に続けて "!" と修飾子クラスの完全修飾名で表されます。

  - ELEMENT_TYPE_SZARRAY は、配列の要素型に続けて "[]" と表されます。

  - ELEMENT_TYPE_GENERICARRAY は、配列の要素型に続けて "[?]" と表されます。 これは C# コンパイラでは生成されません。

  - ELEMENT_TYPE_ARRAY は、[*lowerbound*:`size`,*lowerbound*:`size`] の形式で表されます。ここで、コンマの個数はランク -1 個であり、各次元の下限とサイズは明らかな場合は、10 進数で表されます。 下限またはサイズの指定がない場合は省略されます。 特定の次元で下限およびサイズが省略されている場合は、':' も省略されます。 たとえば、ある 2 次元配列の下限が 1 で、サイズの指定がない場合は、[1:,1:] と表されます。

  - ELEMENT_TYPE_FNPTR は、"=FUNC:`type`(*signature*)" と表されます。ここで、`type` は戻り値の型であり、*signature* はメソッドの引数です。 引数がない場合、かっこは省略されます。 これは C# コンパイラでは生成されません。

  次に示すシグネチャ コンポーネントは、オーバーロードされるメソッドの区別には使用されないため、表されません。

  - 呼び出し規則

  - 戻り値の型

  - ELEMENT_TYPE_SENTINEL

- 変換演算子 (`op_Implicit` および `op_Explicit`) の場合のみ、メソッドの戻り値が "~" としてエンコードされ、それに続けて戻り値の型が表されます。

- ジェネリック型では、型の名前の後に、バックチック、ジェネリック型パラメーターの数を示す数値が順に続きます。 次に例を示します。

     ``<member name="T:SampleClass`2">`` は、`public class SampleClass<T, U>` として定義されている型のタグです。

     パラメーターとしてジェネリック型を受け取るメソッドでは、ジェネリック型パラメーターは、バックチック付きの数値 (\`0、\`1 など) として指定されます。 各数値は、型のジェネリック パラメーターに対する、0 から始まる配列表記を表しています。

## <a name="examples"></a>使用例

次の例は、クラスおよびそのメンバーの ID 文字列を生成する方法を示します。

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [-doc (C# コンパイラ オプション)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML ドキュメント コメント](./index.md)
