---
title: Visual Studio Code での F# の概要
description: 'Visual Studio Code と Ionide plugin suite で F # を使用する方法について説明します。'
ms.date: 12/23/2018
ms.openlocfilehash: 11fb0d443fb7c2b3f270d45bfeaa91102ba28efd
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739803"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Visual Studio Code での F# の概要

[Ionide プラグイン](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)を使用して[Visual Studio Code](https://code.visualstudio.com)に F # を記述すると、IntelliSense とコードリファクタリングを使用して、優れたクロスプラットフォームで軽量の統合開発環境 (IDE) エクスペリエンスを実現できます。 プラグインの詳細については、 [Ionide.io](https://ionide.io) を参照してください。

開始するには、 [F # と Ionide プラグインが正しくインストールさ](install-fsharp.md#install-f-with-visual-studio-code)れていることを確認します。

## <a name="create-your-first-project-with-ionide"></a>Ionide を使用して最初のプロジェクトを作成する

新しい F # プロジェクトを作成するには、コマンドラインを開き、.NET Core CLI を使用して新しいプロジェクトを作成します。

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

完了したら、ディレクトリをプロジェクトに変更し、Visual Studio Code を開きます。

```console
cd FirstIonideProject
code .
```

Visual Studio Code にプロジェクトが読み込まれると、ウィンドウの左側に [F # ソリューションエクスプローラー] ウィンドウが表示されます。 これは、Ionide によって作成したプロジェクトが正常に読み込まれたことを意味します。 この時点より前に、エディターでコードを記述できますが、これが発生すると、すべての読み込みが完了します。

## <a name="configure-f-interactive"></a>F # interactive の構成

最初に、.NET Core スクリプトが既定のスクリプト環境であることを確認します。

1. Visual Studio Code 設定 ([**コード**  >  **設定]**  >  **設定**) を開きます。
1. 「 **F # スクリプト**」という用語を検索します。
1. **「Fsharp.core: USE SDK scripts**」というチェックボックスをオンにします。

これは現在、.NET Core スクリプトでは動作しない .NET Framework ベースのスクリプトのいくつかのレガシ動作のために必要です。また、Ionide は現在、旧バージョンとの互換性を維持するために努力しています。 今後、.NET Core スクリプトが既定値になります。

### <a name="write-your-first-script"></a>最初のスクリプトを作成する

.NET Core スクリプトを使用するように Visual Studio Code を構成したら、Visual Studio Code の [エクスプローラー] ビューに移動し、新しいファイルを作成します。 名前を *MyFirstScript script.fsx* にします。

ここで、次のコードを追加します。

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

この関数は、単語を [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)の形式に変換します。 次の手順では、F# インタラクティブ (FSI.EXE) を使用して評価します。

関数全体を強調表示します (11 行の長さである必要があります)。 強調表示されたら、 **Alt** キーを押しながら **Enter** キーを押します。 画面の下部にターミナルウィンドウがポップアップ表示され、次のように表示されます。

![Ionide を使用した F# インタラクティブ出力の例](./media/getting-started-vscode/vscode-fsi.png)

これは次の3つの処理を行いました。

1. FSI.EXE プロセスを開始しました。
2. FSI.EXE プロセスで強調表示したコードが送信されました。
3. FSI.EXE プロセスは、送信したコードを評価しました。

送信したのは [関数](../language-reference/functions/index.md)だったので、fsi.exe! を使用してその関数を呼び出すことができるようになりました。 対話型ウィンドウで、次のように入力します。

```fsharp
toPigLatin "banana";;
```

次の結果が表示されます。

```fsharp
val it : string = "ananabay"
```

では、最初の文字として母音を試してみましょう。 次のように入力します。

```fsharp
toPigLatin "apple";;
```

次の結果が表示されます。

```fsharp
val it : string = "appleyay"
```

関数が想定どおりに動作しているようです。 これで、最初の F # 関数を Visual Studio Code に記述し、FSI.EXE を使用して評価しました。

> [!NOTE]
> ご存知かもしれませんが、FSI.EXE の行はで終了 `;;` します。 これは、FSI.EXE で複数の行を入力できるためです。 `;;`最後のは、コードが終了したことを fsi.exe に通知します。

## <a name="explaining-the-code"></a>コードの説明

実際にコードが何をしているかわからない場合は、次の手順を実行します。

ご覧のように、 `toPigLatin` は単語を入力として受け取り、その単語の Pig-Latin 表現に変換する関数です。 この規則は次のとおりです。

単語の最初の文字が母音で始まる場合は、単語の末尾に "yay" を追加します。 母音で始まらない場合は、その最初の文字を単語の末尾に移動し、それに "ay" を追加します。

FSI.EXE では、次のことにご気になるかもしれません。

```fsharp
val toPigLatin : word:string -> string
```

これ `toPigLatin` は、を `string` 入力として受け取り (と呼びます)、別のを返す関数であることを示し `word` `string` ます。 これは、f # コードを理解するうえで重要な F # の基本的な部分である [関数の型シグネチャ](https://fsharpforfunandprofit.com/posts/function-signatures/)と呼ばれています。 Visual Studio Code で関数をポイントすると、この点にも注意してください。

関数の本体には、次の2つの異なる部分があります。

1. 指定した `isVowel` 文字 () が、指定された `c` パターンのいずれかと一致 [するか](../language-reference/pattern-matching.md)どうかをチェックすることによって、特定の文字 () が母音であるかどうかを判断する内部関数。

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)最初の文字が母音であるかどうかを確認し、最初の文字が母音であるかどうかに基づいて、入力文字から戻り値を構築する式。

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

そのため、のフロー `toPigLatin` は次のようになります。

入力単語の最初の文字が母音であるかどうかを確認します。 の場合は、単語の末尾に "yay" を付加します。 それ以外の場合は、最初の文字を単語の末尾に移動し、それに "ay" を追加します。

この点については最後に説明します。 F # では、関数から戻る明示的な命令がありません。 これは、F # が式ベースであり、関数の本体で評価された最後の式によってその関数の戻り値が決定されるためです。 `if..then..else`はそれ自体が式であるため、ブロックの本体 `then` またはブロックの本体の評価に `else` よって、関数によって返される値が決まり `toPigLatin` ます。

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a>コンソールアプリを Pig Latin ジェネレーターにする

この記事の前のセクションでは、F # コードを記述するための一般的な最初の手順を示しています。初期関数を記述し、FSI.EXE を使用して対話形式で実行します。 これは REPL ドリブン開発と呼ばれます。 [repl](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) は "Read Evaluate-Print Loop" を表します。 機能を使用するには、機能を試してみることをお勧めします。

REPL 駆動型開発の次の手順では、作業コードを F # 実装ファイルに移動します。 その後、これを F # コンパイラでコンパイルして、実行可能なアセンブリにすることができます。

まず、.NET Core CLI で作成した *プログラム* のファイルを開きます。 いくつかのコードが既に存在していることがわかります。

次に、という新しいを作成 [`module`](../language-reference/modules.md) `PigLatin` し、 `toPigLatin` 先ほど作成した関数を次のようにコピーします。

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

このモジュールは、関数の上と宣言の下に配置する必要があり `main` `open System` ます。 F # では宣言の順序が重要であるため、関数をファイルで呼び出す前に定義する必要があります。

次に、関数で、 `main` 引数に対して Pig Latin generator 関数を呼び出します。

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn %"{name} in Pig Latin is: {newName}"

    0
```

これで、コマンドラインからコンソールアプリを実行できるようになりました。

```dotnetcli
dotnet run apple banana
```

スクリプトファイルと同じ結果が出力されますが、今回は実行中のプログラムとして出力されます。

## <a name="troubleshooting-ionide"></a>Ionide のトラブルシューティング

発生する可能性がある特定の問題をトラブルシューティングするには、次のいくつかの方法があります。

1. Ionide のコード編集機能を利用するには、F # ファイルをディスクに保存し、[Visual Studio Code] ワークスペースで開いているフォルダー内に保存する必要があります。
1. システムに変更を加えた場合、または Visual Studio Code を開いた状態でインストールされた Ionide の前提条件を確認した場合は、Visual Studio Code を再起動します。
1. プロジェクトディレクトリに無効な文字が含まれていると、Ionide が機能しない可能性があります。  この場合は、プロジェクトディレクトリの名前を変更します。
1. Ionide コマンドがいずれも動作していない場合は、 [Visual Studio Code キーバインド](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) を調べて、誤って上書きしているかどうかを確認します。
1. Ionide がコンピューター上で破損していて、上記のいずれも問題を解決していない場合は、 `ionide-fsharp` コンピューター上のディレクトリを削除し、プラグインスイートを再インストールしてみてください。
1. プロジェクトの読み込みに失敗した場合 (F # ソリューションエクスプローラーによって表示されます)、そのプロジェクトを右クリックし、[ **詳細の表示** ] をクリックして診断情報を取得します。

Ionide は、F # コミュニティのメンバーによって構築および管理されるオープンソースプロジェクトです。 問題を報告して、 [ionide-vscode-Fsharp.core GitHub リポジトリ](https://github.com/ionide/ionide-vscode-fsharp)に投稿してください。

[Ionide Gitter チャネル](https://gitter.im/ionide/ionide-project)の Ionide 開発者や F # コミュニティから、さらに支援を求めることもできます。

## <a name="next-steps"></a>次のステップ

F # とその言語の機能の詳細については、「 [f # のツアー](../tour.md)」を参照してください。
