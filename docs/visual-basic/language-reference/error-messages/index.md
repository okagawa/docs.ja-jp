---
description: '詳細情報: Visual Basic のエラー メッセージ'
title: Visual Basic のエラー メッセージ
titleSuffix: ''
ms.date: 10/13/2020
helpviewer_keywords:
- errors [Visual Basic]
- error messages
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 28e59a47c47ff7905dfec93b057f7cb534842b91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796068"
---
# <a name="error-messages-in-visual-basic"></a>Visual Basic のエラー メッセージ

Visual Basic アプリケーションをコンパイルまたは実行する際は、次の種類のエラーが発生する可能性があります。

- コンパイル時エラー。アプリケーションをコンパイルするときに発生します。

- 実行時エラー。アプリケーションの実行中に発生します。

特定のエラーのトラブルシューティング方法については、「[Visual Basic プログラマのための追加リソース](../../getting-started/additional-resources.md)」を参照してください。

## <a name="run-time-errors"></a>実行時エラー

Visual Basic アプリケーションがシステムで実行できないアクションを実行しようとすると、実行時エラーが発生し、Visual Basic によって <xref:System.Exception> オブジェクトがスローされます。 Visual Basic では、`Throw` ステートメントを使用することで、`Exception` オブジェクトを含む任意のデータ型のカスタム エラーを生成できます。 アプリケーションは、キャッチされた例外のエラー番号とメッセージを表示して、エラーを識別できます。 エラーがキャッチされない場合、アプリケーションは終了します。

実行時エラーはコードでトラップして調べることができます。 エラーが発生するコードを `Try` ブロックで囲むと、スローされたエラーを対応する `Catch` ブロック内でキャッチできます。 実行時にエラーをトラップしてコードで対処する方法については、「[Try...Catch...Finally ステートメント](../statements/try-catch-finally-statement.md)」を参照してください。

## <a name="compile-time-errors"></a>コンパイル時のエラー

Visual Basic コンパイラがコード内で問題を検出すると、コンパイル時エラーが発生します。 Visual Studio コード エディターでは、エラーの原因となったコード行の下に波線が表示されるため、簡単にその行を特定できます。 波線をポイントするか **エラー一覧** を開くと、エラー メッセージが表示されます。エラー一覧には他のメッセージも表示されます。

識別子の下に波線があり、右端の文字の下に短い下線が表示されている場合は、クラス、コンストラクター、メソッド、プロパティ、フィールド、または列挙型のスタブを生成できます。 詳細については、[使用法からの生成 (Visual Studio)](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage) に関する記事を参照してください。

Visual Basic コンパイラからのエラーを解決することにより、高速に実行されるバグの少ないコードを作成できます。 これらの警告では、アプリケーションの実行時にエラーを発生させるコードが示されます。 たとえば、ユーザーが、割り当てが行われていないオブジェクト変数のメンバーを呼び出そうとしたり、戻り値を設定せずに関数から戻ろうとしたり、例外をキャッチするロジックにエラーがある `Try` ブロックを実行しようとしたりすると、コンパイラは警告を表示します。 警告の表示/非表示を切り替える方法など、警告の詳細については、「[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。
