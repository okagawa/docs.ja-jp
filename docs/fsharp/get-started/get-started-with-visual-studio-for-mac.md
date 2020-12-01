---
title: 'Visual Studio for Mac で F # を使ってみる'
description: 'Visual Studio for Mac で F # を使用する方法について説明します。'
ms.date: 07/03/2018
ms.openlocfilehash: d2ad24ad18bb31419b39508f2cf555c82fbe2e0b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437989"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Visual Studio for Mac で F # を使ってみる

F # と Visual F# ツールは、Visual Studio for Mac IDE でサポートされています。 [Visual Studio for Mac がインストールされ](install-fsharp.md#install-f-with-visual-studio-for-mac)ていることを確認します。

## <a name="creating-a-console-application"></a>コンソールアプリケーションの作成

Visual Studio for Mac の最も基本的なプロジェクトの1つは、コンソールアプリケーションです。  その方法を次に示します。  Visual Studio for Mac が開いたら、次のようになります。

1. [ **ファイル** ] メニューの [ **新しいソリューション**] をポイントします。

2. [新しいプロジェクト] ダイアログには、コンソールアプリケーションに2つの異なるテンプレートがあります。  .NET Framework をターゲットとする > .NET の下に1つあります。  その他のテンプレートは .net core > アプリの下にあり、.NET Core を対象としています。  どちらのテンプレートも、この記事の目的で機能します。

3. [コンソールアプリ] で、必要に応じて C# を F # に変更します。  [ **次へ** ] ボタンをクリックして先に進みます。  

4. プロジェクトに名前を付け、アプリに必要なオプションを選択します。  プレビューウィンドウには、選択したオプションに基づいて作成されるディレクトリ構造が表示されます。  

5. **[作成]** をクリックします。  ソリューションエクスプローラーに F # プロジェクトが表示されます。

## <a name="writing-your-code"></a>コードの記述

まず、コードをいくつか記述してみましょう。  ファイルが開いていることを確認し、 `Program.fs` その内容を次の内容に置き換えます。

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

前のコードサンプルでは、と `square` いう名前の入力を受け取り、それを単独で乗算する関数が定義されてい `x` ます。  F # では [型の推定](../language-reference/type-inference.md)が使用されるため、の型を `x` 指定する必要はありません。  F # コンパイラは、乗算が有効な型を認識し、 `x` が呼び出される方法に基づいて型をに割り当て `square` ます。  マウスポインターを合わせると `square` 、次のように表示されます。

```console
val square: x:int -> int
```

これは、関数の型シグネチャとして知られています。  これは、次のように読み取ることができます。 "Square は、x という整数を受け取り、整数を生成する関数です。"  コンパイラによって型が設定されていることに注意して `square` `int` ください。これは、乗算が *すべて* の型のジェネリックではなく、閉じられた型のセット全体でジェネリックであるためです。  この時点で F # コンパイラは選択されていますが、などの別の入力型を使用してを `int` 呼び出すと、型シグネチャが調整され `square` `float` ます。

もう1つの関数 `main` が定義されています。これは、 `EntryPoint` プログラムの実行が開始される必要があることを F # コンパイラに通知する属性で修飾されています。  これは、コマンドライン引数をこの関数に渡すことができる他の [C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)と同じ規則に従い、整数のコードが返されます (通常は `0` )。

この関数は、引数を指定して `square` 関数を呼び出し `12` ます。  次に F # コンパイラは、の型 `square` をに割り当て `int -> int` ます。これは、を受け取り、を生成する関数です `int` `int` 。  の呼び出しは、書式指定文字列を使用する書式 `printfn` 設定された印刷関数で、C スタイルのプログラミング言語に似ています。また、書式指定文字列で指定されたパラメーターに対応するパラメーターを使用して、結果と改行を出力します。

## <a name="running-your-code"></a>コードの実行

上部のメニューから [ **実行** ] をクリックし、[ **デバッグなしで開始**] をクリックして、コードを実行し、結果を確認できます。  これにより、デバッグなしでプログラムが実行され、結果を確認できるようになります。

コンソールウィンドウに次の出力が表示され、Visual Studio for Mac ポップアップされます。

```console
12 squared is 144!
```

お疲れさまでした。  最初の F # プロジェクトを Visual Studio for Mac で作成し、その関数を呼び出した結果を出力する F # 関数を記述し、プロジェクトを実行して結果を確認しました。

## <a name="using-f-interactive"></a>F# インタラクティブの使用

Visual Studio for Mac の Visual F# ツールの最適な機能の1つは、F# インタラクティブウィンドウです。  このメソッドを使用すると、コードを呼び出して結果を対話形式で確認できるプロセスにコードを送信できます。

使用を開始するには、 `square` コードで定義されている関数を強調表示します。  次に、トップレベルメニューの [ **編集** ] をクリックします。  次 **に、[選択範囲を F# インタラクティブに送信**] を選択します。  これにより、[F# インタラクティブ] ウィンドウのコードが実行されます。  または、選択範囲を右クリックし、[ **選択項目を F# インタラクティブに送信**] を選択します。  [F# インタラクティブ] ウィンドウが表示され、次のようなウィンドウが表示されます。

```console
>

val square : x:int -> int

>
```

これは、関数をポイントしたときに前に見た関数の関数シグネチャと同じ `square` です。  `square`は現在 F# インタラクティブプロセスで定義されているため、異なる値を使用して呼び出すことができます。

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

これにより、関数が実行され、結果が新しい名前にバインドされ、 `it` の型と値が表示され `it` ます。  各行は、で終了する必要があることに注意 `;;` してください。  これは、関数呼び出しがいつ終了するかを F# インタラクティブが認識する方法です。  F# インタラクティブで新しい関数を定義することもできます。

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上のでは新しい関数が定義されています `isOdd` 。これはを受け取り、 `int` それが奇数かどうかを確認します。  この関数を呼び出すと、異なる入力で何が返されるかを確認できます。  関数呼び出しの中で関数を呼び出すことができます。

```console
> isOdd (square 15);;
val it : bool = true
```

[パイプ転送演算子](../language-reference/symbol-and-operator-reference/index.md)を使用して、値を次の2つの関数にパイプライン処理することもできます。

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

パイプ転送演算子などの詳細については、以降のチュートリアルで説明します。

これは、F# インタラクティブでできることだけを示しています。  詳細については、 [F # を使用した対話型プログラミングに関する](../tools/fsharp-interactive/index.md)ページをご覧ください。

## <a name="next-steps"></a>次のステップ

F # 言語のコア機能の一部については、「 [f # のツアー](../tour.md)」をご覧ください。  ここでは、F # の一部の機能の概要を説明し、Visual Studio for Mac にコピーして実行できるコードサンプルをいくつか紹介します。  また、 [F # ガイド](../index.yml)に記載されている、使用できる優れた外部リソースもあります。

## <a name="see-also"></a>関連項目

- [F# ガイド](../index.yml)
- [F# のツアー](../tour.md)
- [F# 言語リファレンス](../language-reference/index.md)
- [型の推論](../language-reference/type-inference.md)
- [シンボルと演算子のリファレンス](../language-reference/symbol-and-operator-reference/index.md)
