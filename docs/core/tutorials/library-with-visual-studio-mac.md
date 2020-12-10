---
title: Visual Studio for Mac を使用して .NET クラス ライブラリを作成する
description: Visual Studio for Mac を使用して .NET クラス ライブラリを作成する方法について学習します。
ms.date: 11/30/2020
ms.openlocfilehash: 1b6b26de06d18d505fa6dde3ff9779a3dab3f1e6
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599306"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-for-mac"></a>チュートリアル: Visual Studio for Mac を使用して .NET クラス ライブラリを作成する

このチュートリアルでは、1 つの文字列処理メソッドを含むクラス ライブラリを作成します。

"*クラス ライブラリ*" は、アプリケーションから呼び出される型とメソッドを定義します。 ライブラリのターゲットが .NET Standard 2.0 である場合は、.NET Standard 2.0 をサポートする任意の .NET 実装 (.NET Framework を含む) で呼び出すことができます。 ライブラリのターゲットが .NET 5 である場合は、.NET 5 をターゲットとする任意のアプリケーションで呼び出すことができます。 このチュートリアルでは、.NET 5 をターゲットとする方法を示します。

> [!NOTE]
> お客様のフィードバックは非常に貴重です。 次の 2 つの方法で Visual Studio for Mac の開発チームにフィードバックを送信できます。
>
> - Visual Studio for Mac で、メニューから **[ヘルプ]**  >  **[問題の報告]** の順に選択するか、ようこそ画面から **[問題の報告]** を選択して、バグ報告を提出するためのウィンドウを開きます。 お客様のフィードバックは、[開発者コミュニティ](https://aka.ms/feedback/report?space=41) ポータルで追跡することができます。
> - 提案するには、メニューから **[ヘルプ]**  >  **[提案の送信]** の順に選択するか、ようこそ画面から **[提案の送信]** を選択し、[Visual Studio for Mac の開発者コミュニティの Web ページ](https://aka.ms/feedback/suggest?space=41)に移動します。

## <a name="prerequisites"></a>必須コンポーネント

* [Visual Studio for Mac バージョン 8.8 以降をインストールします](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。 .NET Core をインストールするオプションを選択します。 .NET 開発の場合、Xamarin のインストールは省略可能です。 詳細については、次のリソースを参照してください。

  * [チュートリアル: Visual Studio for Mac をインストールする](/visualstudio/mac/installation)。
  * [サポート対象の macOS のバージョン](../install/macos.md)。
  * [Visual Studio for Mac でサポートされている .NET のバージョン](/visualstudio/mac/net-core-support)。

## <a name="create-a-solution-with-a-class-library-project"></a>クラス ライブラリ プロジェクトを含むソリューションの作成

1 つの Visual Studio のソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。 ソリューションと、そのソリューション内のクラス ライブラリ プロジェクトを作成します。 後ほど、さらに関連するプロジェクトを同じソリューションに追加します。

1. Visual Studio for Mac を起動します。

1. スタート ウィンドウで、 **[新しいプロジェクト]** を選択します。

1. **[新しいプロジェクト用のテンプレートを選びます]** ダイアログで、 **[Web and Console]\(Web とコンソール\)**  >  **[ライブラリ]**  >  **[クラス ライブラリ]** の順に選択した後、 **[次へ]** を選択します。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="[新しいプロジェクト] ダイアログ":::

1. **[Configure your new Class Library]\(新しいクラス ライブラリの構成\)** ダイアログで、 **[.NET 5.0]** を選択し、 **[次へ]** を選択します。

1. プロジェクトに「StringLibrary」という名前を指定し、ソリューションに「ClassLibraryProjects」という名前を指定します。 **[ソリューション ディレクトリ内にプロジェクト ディレクトリを作成する]** はオンのままにしておきます。 **[作成]** を選択します。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Visual Studio for Mac の [新しいプロジェクト] ダイアログのオプション":::

1. メイン メニューから **[表示]**  >  **[ソリューション]** の順に選択し、ドッキング アイコンを選択してパッドを開いたままにします。

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="ソリューション パッドのドッキング アイコン":::

1. **[ソリューション]** パッドで、`StringLibrary` ノードを展開し、テンプレートで提供される *Class1.cs* というクラス ファイルを表示します。 <kbd>ctrl</kbd> キーを押しながらファイルをクリックし、コンテキスト メニューから **[名前の変更]** を選択して、ファイル名を *StringLibrary.cs* に変更します。 ファイルを開き、内容を次のコードに置き換えます。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd> + <kbd>S</kbd>) キーを押して、ファイルを保存します。

1. IDE ウィンドウの下部の余白にある **[エラー]** を選択して、 **[エラー]** パネルを開きます。 **[ビルド出力]** ボタンを選択します。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="[エラー] ボタンが示された Visual Studio Mac IDE の下部余白":::

1. メニューから **[ビルド]**  >  **[すべてビルド]** の順に選択します。

   ソリューションがビルドされます。 ビルド出力パネルに、ビルドが成功したことが示されます。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="ビルドの成功メッセージが表示された、[エラー] パネルの Visual Studio Mac のビルド出力ウィンドウ":::

## <a name="add-a-console-app-to-the-solution"></a>ソリューションにコンソール アプリを追加する

このクラス ライブラリを使用するコンソール アプリケーションを追加します。 アプリによって、ユーザーに文字列の入力が求められ、文字列が大文字で始まるかどうかが報告されます。

1. **[ソリューション]** パッドで、<kbd>ctrl</kbd> キーを押しながら `ClassLibraryProjects` ソリューションをクリックします。 **[Web and Console]\(Web とコンソール\)**  >  **[アプリ]** テンプレートからテンプレートを選択することで、新しい **[コンソール アプリケーション]** プロジェクトを追加し、 **[次へ]** を選択します。

1. **[ターゲット フレームワーク]** として **[.NET 5.0]** を選択し、 **[次へ]** を選択します。

1. プロジェクトに「**ShowCase**」という名前を付けます。 **[作成]** を選択し、ソリューションでプロジェクトを作成します。

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="ShowCase プロジェクトを追加する":::

1. *Program.cs* ファイルを開きます。 このコードを次のコードに置き換えます。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   プログラムは、ユーザーに文字列の入力を要求し、 文字列が大文字で始まるかどうかを示します。 ユーザーが文字列を入力せずに <kbd>enter</kbd> キーを押すと、アプリケーションが終了し、コンソール ウィンドウが閉じます。

   このコードでは、`row` 変数を使って、コンソール ウィンドウに書き込まれるデータの行数のカウントを維持します。 これが 25 以上になると、コードによってコンソール ウィンドウがクリアされ、ユーザーにメッセージが表示されます。

## <a name="add-a-project-reference"></a>プロジェクト参照を追加する

最初は、新しいコンソール アプリ プロジェクトにクラス ライブラリへのアクセス権はありません。 クラス ライブラリでメソッドを呼び出せるようにするには、クラス ライブラリ プロジェクトへのプロジェクト参照を作成します。

1. **[ソリューション]** パッドで、<kbd>ctrl</kbd> キーを押しながら、新しい **ShowCase** プロジェクトの **[依存関係]** ノードをクリックします。 コンテキスト メニューから **[参照の追加]** を選択します。

1. **[参照]** ダイアログで、 **[StringLibrary]** を選択して **[OK]** を選択します。

## <a name="run-the-app"></a>アプリを実行する

1. <kbd>ctrl</kbd> キーを押しながら **ShowCase** プロジェクトをクリックし、コンテキスト メニューから **[プロジェクトの実行]** を選択します。

1. 文字列を入力して <kbd>enter</kbd> キーを押すことでプログラムを試してみます。<kbd>enter</kbd> キーを押して終了します。

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="アプリが実行中であることを示す Visual Studio for Mac のコンソール ウィンドウ":::

## <a name="additional-resources"></a>その他の技術情報

* [.NET CLI を使用してライブラリを開発する](libraries.md)
* [Visual Studio 2019 for Mac リリース ノート](/visualstudio/releasenotes/vs2019-mac-relnotes)
* [.NET Standard のバージョンとそれらでサポートされているプラットフォーム](../../standard/net-standard.md)。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、ソリューションとライブラリ プロジェクトを作成し、そのライブラリを使用するコンソール アプリ プロジェクトを追加しました。 次のチュートリアルでは、ソリューションに単体テスト プロジェクトを追加します。

> [!div class="nextstepaction"]
> [Visual Studio for Mac を使用して .NET クラス ライブラリをテストする](testing-library-with-visual-studio-mac.md)
