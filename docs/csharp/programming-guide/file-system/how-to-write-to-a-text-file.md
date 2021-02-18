---
title: テキスト ファイルに書き込む方法 - C# プログラミング ガイド
description: C# でテキスト ファイルを記述する方法について説明します。 いくつかのコード例を参照し、使用可能なその他のリソースを確認してください。
ms.date: 02/11/2021
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.topic: how-to
ms.custom: contperf-fy21q3
ms.openlocfilehash: ecc3ba73161d4f4571bbc6ae0c9aaa3337586ef7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475618"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>テキスト ファイルに書き込む方法 (C# プログラミング ガイド)

この記事では、ファイルにテキストを書き込むさまざまな方法の例をいくつか示します。 最初の 2 つの例では、<xref:System.IO.File?displayProperty=nameWithType> クラスの便利な静的メソッドを使用し、すべての `IEnumerable<string>` の各要素と `string` をテキスト ファイルに書き込みます。 3 番目の例では、ファイルに書き込みながら各行を個別に処理する必要がある場合にテキストをファイルに追加する方法を示します。 最初の 3 つの例では、ファイルの既存のコンテンツはすべて上書きします。 最後の例では、テキストを既存のファイルに追加する方法を示します。

 これらの例はいずれもリテラル文字列をファイルに書き込みます。 ファイルに書き込まれるテキストの書式を設定する場合は、<xref:System.String.Format%2A> メソッドまたは C# の[文字列補間](../../language-reference/tokens/interpolated.md)機能を使用します。

## <a name="write-a-collection-of-strings-to-a-file"></a>ファイルに文字列のコレクションを書き込む

:::code language="csharp" source="snippets/write-text/WriteAllLines.cs":::

上記のソース コードの例では、次を行います。

- 3 つの値で文字列の配列をインスタンス化します。
- 次を行う、<xref:System.IO.File.WriteAllLinesAsync%2A?displayProperty=nameWithType> に対する呼び出しを待機します。

  - 非同期的に *WriteLines.txt* という名前のファイルを作成します。 既にある場合は、ファイルは上書きされます。
  - ファイルに指定した行を書き込みます。
  - 必要に応じて、自動的にフラッシュおよび破棄し、ファイルを閉じます。

## <a name="write-one-string-to-a-file"></a>ファイルに文字列を 1 つ書き込む

:::code language="csharp" source="snippets/write-text/WriteAllText.cs":::

上記のソース コードの例では、次を行います。

- 割り当てられた文字列リテラルを指定して、文字列をインスタンス化します。
- 次を行う、<xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> に対する呼び出しを待機します。

  - 非同期的に *WriteText.txt* という名前のファイルを作成します。 既にある場合は、ファイルは上書きされます。
  - 指定したテキストをファイルに書き込みます。
  - 必要に応じて、自動的にフラッシュおよび破棄し、ファイルを閉じます。

## <a name="write-selected-strings-from-an-array-to-a-file"></a>選択した文字列を配列からファイルに書き込む

:::code language="csharp" source="snippets/write-text/StreamWriterOne.cs":::

上記のソース コードの例では、次を行います。

- 3 つの値で文字列の配列をインスタンス化します。
- [using 宣言](../../whats-new/csharp-8.md#using-declarations)として *WriteLines2.txt* のファイル パスを使用して <xref:System.IO.StreamWriter> をインスタンス化します。
- すべての行を反復処理します。
- 行に `"Second"` が含まれないときに、ファイルに行を書き込む <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType> に対する呼び出しを条件付きで待機します。

## <a name="append-text-to-an-existing-file"></a>既存のファイルにテキストを追加する

:::code language="csharp" source="snippets/write-text/StreamWriterTwo.cs":::

上記のソース コードの例では、次を行います。

- 3 つの値で文字列の配列をインスタンス化します。
- [using 宣言](../../whats-new/csharp-8.md#using-declarations)として *WriteLines2.txt* のファイル パスを使用し、追加するために `true` を渡して <xref:System.IO.StreamWriter> をインスタンス化します。
- 文字列を追加された行としてファイルに書き込む、<xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType> に対する呼び出しを待機します。

## <a name="exceptions"></a>例外

次の条件を満たす場合は、例外が発生する可能性があります。

- <xref:System.InvalidOperationException>: ファイルは存在するが、読み取り専用である。
- <xref:System.IO.PathTooLongException>: パス名が長すぎる。
- <xref:System.IO.IOException>: ディスクがいっぱいになっている。

ファイル システムの操作時に例外が発生する可能性がある条件は他にもあるため、防御的なプログラムを書くことをお勧めします。

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ファイル システムとレジストリ (C# プログラミング ガイド)](./index.md)
- [サンプル: コレクションをアプリケーション ストレージに保存する](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
