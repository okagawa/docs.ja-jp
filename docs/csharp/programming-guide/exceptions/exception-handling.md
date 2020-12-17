---
title: 例外処理 - C# プログラミング ガイド
description: 例外処理について説明します。 try-catch、try-finally、および try-catch-finally ステートメントの例を確認してください。
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: fabf1413ba498232e67f45460195fe96e25fab0a
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110196"
---
# <a name="exception-handling-c-programming-guide"></a>例外処理 (C# プログラミング ガイド)

[try](../../language-reference/keywords/try-catch.md) ブロックは、例外の影響を受ける可能性があるコードを区分化するために、 C# プログラマによって使用されます。 関連付けられた [catch](../../language-reference/keywords/try-catch.md) ブロックは、スローされた例外を処理するために使用されます。 [finally](../../language-reference/keywords/try-finally.md) ブロックには、`try` ブロックで例外がスローされたかどうかにかかわらず実行されるコードが含まれます (`try` ブロックに割り当てられたリソースの解放など)。 `try` ブロックには、1 つ以上の `catch` ブロック、`finally` ブロック、またはその両方が関連付けられる必要があります。

次のコードは、`try-catch` ステートメント、`try-finally` ステートメント、および `try-catch-finally` ステートメントの例です。

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryFinallyStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchFinallyStructure":::

`try` ブロックに `catch` または `finally` ブロックがない場合は、コンパイル エラーが発生します。

## <a name="catch-blocks"></a>catch ブロック

`catch` ブロックでは、キャッチする例外の種類を指定できます。 この型指定は、*例外フィルター* と呼ばれます。 例外の種類は、<xref:System.Exception> から派生している必要があります。 一般に、`try` ブロックからスローされる可能性があるすべての例外の処理方法を把握している場合や、`catch` ブロックの末尾に [throw](../../language-reference/keywords/throw.md) ステートメントが含まれている場合を除いては、例外フィルターとして <xref:System.Exception> を指定しないでください。

複数の `catch` ブロックに異なる例外クラスが含まれている場合は、それらを連結することができます。 `catch` ブロックはコード内で上から下に評価されますが、スローされた各例外に対して実行される `catch` ブロックは 1 つだけです。 スローされた例外の厳密な型か、その基底クラスを指定する最初の `catch` ブロックが実行されます。 一致する例外クラスを指定した `catch` ブロックがない場合は、種類のない `catch` ブロックが選択されます (それがステートメント内に存在する場合)。 最初に配置する `catch` ブロックでは、最も具体的な (つまり、最も派生した) 例外クラスを指定することが重要です。

次の条件に該当する場合は、例外をキャッチします。

- 例外がスローされる理由を十分に理解していて、かつ特定の回復手段を実装できる (<xref:System.IO.FileNotFoundException> オブジェクトをキャッチした場合に、ユーザーに新しいファイル名を入力するよう求めるなど)。
- より具体的な例外を新規に作成し、スローできる。
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="ThrowMoreSpecificException":::
- 例外を追加処理に渡す前に、その例外を部分的に処理する必要がある。 次の例では、例外を再スローする前に、エラー ログにエントリを追加する目的で `catch` ブロックが使用されています。
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="RethrowError":::

"*例外フィルター*" を指定して、catch 句にブール式を追加することもできます。 これは、特定の catch 句が、その条件が true の場合にのみ一致することを示します。 次の例では、両方の catch 句で同じ例外クラスが使用されますが、追加の条件が確認され、別のエラー メッセージが作成されます。

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="DemonstrateExceptionFilter":::

常に `false` を返す例外フィルターを使用すると、すべての例外を検証できますが、処理は行われません。 通常は、例外をログに記録するために使用します。

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="ShowExceptionFilter":::

`LogException` メソッドにより常に `false` が返され、この例外フィルターを使用する `catch` 句は一致しません。 catch 句は一般的なもので (<xref:System.Exception?displayProperty=nameWithType> を使用)、後の句によってより具体的な例外クラスを処理することができます。

## <a name="finally-blocks"></a>Finally ブロック

`finally` ブロックでは、`try` ブロックで実行されるアクションをクリーンアップすることができます。 `finally` ブロック (存在する場合) は、最後 (`try` ブロックおよび一致する `catch` ブロックの後) に実行されます。 `finally` ブロックは、例外がスローされたかどうか、または例外の種類に一致する `catch` ブロックが見つかったかどうかにかかわらず、常に実行されます。

`finally` ブロックは、ランタイム内のガベージ コレクターによってオブジェクトがファイナライズされるのを待つことなく、ファイル ストリーム、データベース接続、グラフィックス ハンドルなどのリソースを解放するために使用できます。 詳細については、[using ステートメント](../../language-reference/keywords/using-statement.md)に関するページを参照してください。

次の例では、`try` ブロックで開かれたファイルを閉じるために `finally` ブロックが使用されています。 ファイルを閉じる前に、ファイル ハンドルの状態が確認されています。 `try` ブロックからファイルを開けなかった場合は、ファイル ハンドルの値が `null` のままになり、`finally` ブロックでファイルが閉じられることはありません。 代わりに、`try` ブロックでファイルが正常に開かれた場合は、`finally` ブロックによって開かれたファイルが閉じられます。

:::code language="csharp" source="snippets/exceptions/Program.cs" id="CleanupIfNotNull":::

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[例外](~/_csharplang/spec/exceptions.md)と [try ステートメント](~/_csharplang/spec/statements.md#the-try-statement)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../../language-reference/index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using ステートメント](../../language-reference/keywords/using-statement.md)
