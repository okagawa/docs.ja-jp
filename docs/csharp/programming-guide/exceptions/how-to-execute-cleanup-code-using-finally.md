---
title: finally を使用してクリーンアップ コードを実行する方法 - C# プログラミング ガイド
description: "'finally' ステートメントを使用してクリーンアップ コードを実行する方法について説明します。 finally ステートメントによって、オブジェクトの必要なクリーンアップが直ちに実行されます。"
ms.date: 12/09/2020
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e9b5d3086488d3f7e3c0709317d6fafd15c439e8
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110183"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>finally を使用してクリーンアップ コードを実行する方法 (C# プログラミング ガイド)

`finally` ステートメントの目的は、例外がスローされた場合でも、オブジェクト (一般に外部リソースを保持しているオブジェクト) に対して必要なクリーンアップをすぐに実行できるようにすることです。 次のように、共通言語ランタイムによってオブジェクトがガベージ コレクションされるまで待機するのではなく、オブジェクトを使用した後すぐに <xref:System.IO.FileStream> で <xref:System.IO.Stream.Close%2A> を呼び出すというのも、このようなクリーンアップの一例です。

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="NoCleanup":::

## <a name="example"></a>例

上のコードを `try-catch-finally` ステートメントに変えるには、次のようにクリーンアップ コードを作業コードから切り離します。

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="WithCleanup":::

`try` ブロック内では `OpenWrite()` 呼び出しの前のどの時点でも例外が発生する可能性があり、また、`OpenWrite()` 呼び出し自体が失敗するおそれもあるため、ファイルを閉じようとしたときに、それが開いているという保証はありません。 `finally` ブロックによって、<xref:System.IO.Stream.Close%2A> メソッドを呼び出す前に、<xref:System.IO.FileStream> オブジェクトが `null` でないことを確認するチェックが追加されます。 この `null` チェックがないと、`finally` ブロックからその <xref:System.NullReferenceException> がスローされる可能性がありますが、`finally` ブロックにおける例外のスローはできるだけ回避する必要があります。

データベース接続も、`finally` ブロックで閉じられる対象になります。 データベース サーバーで許可される接続数は限られていることがあるため、データベース接続はできるだけ早く閉じる必要があります。 接続を閉じる前に例外がスローされる場合は、ガベージ コレクションを待機するより、`finally` ブロックを使用することをお勧めします。

## <a name="see-also"></a>関連項目

- [using ステートメント](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
