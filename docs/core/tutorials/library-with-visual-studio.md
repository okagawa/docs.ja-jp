---
title: Visual Studio を使用して .NET クラス ライブラリを作成する
description: Visual Studio を使用して .NET クラス ライブラリを作成する方法について学習します。
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperf-fy21q1
ms.openlocfilehash: 2d9b02a155c950b77565a66417948568f5fa039f
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513121"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio"></a>チュートリアル: Visual Studio を使用して .NET クラス ライブラリを作成する

このチュートリアルでは、1 つの文字列処理メソッドを含むシンプルなクラス ライブラリを作成します。

"*クラス ライブラリ*" は、アプリケーションから呼び出される型とメソッドを定義します。 ライブラリのターゲットが .NET Standard 2.0 である場合は、.NET Standard 2.0 をサポートする任意の .NET 実装 (.NET Framework を含む) で呼び出すことができます。 ライブラリのターゲットが .NET 5 である場合は、.NET 5 をターゲットとする任意のアプリケーションで呼び出すことができます。 このチュートリアルでは、.NET 5 をターゲットとする方法を示します。

クラス ライブラリを作成するときに、NuGet パッケージとして、またはそれを使用するアプリケーションにバンドルされているコンポーネントとして配布できます。

## <a name="prerequisites"></a>[前提条件]

- **.NET Core クロスプラットフォーム開発** ワークロードがインストールされている [Visual Studio 2019 バージョン 16.8 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 このワークロードを選択すると、.NET 5.0 SDK が自動的にインストールされます。 このチュートリアルでは、 **[[新しいプロジェクト] にすべての .NET Core テンプレートを表示する]** が有効になっていることを前提とします。これについては、「[チュートリアル: Visual Studio を使用して .NET コンソール アプリケーションを作成する](with-visual-studio.md)」を参照してください。

## <a name="create-a-solution"></a>ソリューションを作成する

まず、クラス ライブラリ プロジェクトを配置する空のソリューションを作成します。 1 つの Visual Studio のソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。 さらに関連するプロジェクトを同じソリューションに追加します。

空のソリューションを作成するには:

1. Visual Studio を起動します。

2. スタート ウィンドウで、 **[新しいプロジェクトの作成]** を選択します。

3. **[新しいプロジェクトの作成]** ページで、検索ボックスに「**ソリューション**」と入力します。 **[空のソリューション]** テンプレートを選択して、 **[次へ]** を選択します。

   :::image type="content" source="media/library-with-visual-studio/blank-solution.png" alt-text="Visual Studio での空のソリューション テンプレート":::

4. **[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「**ClassLibraryProjects**」と入力します。 次に、 **[作成]** を選択します。

## <a name="create-a-class-library-project"></a>クラス ライブラリ プロジェクトを作成する

1. "StringLibrary" という名前の新しい .NET クラス ライブラリ プロジェクトをソリューションに追加します。

   1. **ソリューション エクスプローラー** でソリューションを右クリックし、 **[追加]**  >  **[新しいプロジェクト]** の順に選択します。

   1. **[新しいプロジェクトの追加]** ページで、検索ボックスに「**ライブラリ**」と入力します。 言語の一覧から **[C#]** または **[Visual Basic]** を選択し、次に、プラットフォームの一覧から **[すべてのプラットフォーム]** を選択します。 **[クラス ライブラリ]** テンプレートを選んでから、 **[次へ]** を選択します。

   1. **[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「**StringLibrary**」と入力してから、 **[次へ]** を選択します。

   1. **[追加情報]** ページで、 **[.NET 5.0 (Current)]** を選んでから、 **[作成]** を選択します。

1. 確実にライブラリのターゲットが正しいバージョンの .NET になっていることを確かめます。 **ソリューション エクスプローラー** でライブラリ プロジェクトを右クリックし、 **[プロパティ]** を選択します。 **[ターゲット フレームワーク]** テキスト ボックスに、.NET 5.0 がプロジェクトのターゲットになっていることが示されています。

1. Visual Basic を使用している場合は、 **[ルート名前空間]** テキスト ボックス内のテキストをクリアします。

   :::image type="content" source="./media/library-with-visual-studio/vb/library-project-properties.png" alt-text="クラス ライブラリのプロジェクト プロパティ":::

   プロジェクトごとに、そのプロジェクト名に対応する名前空間が Visual Basic によって自動的に作成されます。 このチュートリアルでは、コード ファイルで [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) キーワードを使用して、最上位の名前空間を定義します。

1. *Class1.cs* または *Class1.vb* のコード ウィンドウ内のコードを次のコードに置き換えて、ファイルを保存します。 使用する言語が表示されていない場合は、ページの上部にある言語セレクターを変更します。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   クラス ライブラリ `UtilityLibraries.StringLibrary` には、`StartsWithUpper` という名前のメソッドが含まれています。 このメソッドによって、現在の文字列のインスタンスが大文字で始まるかどうかを示す <xref:System.Boolean> 値が返されます。 Unicode 規格では、大文字と小文字が区別されます。 <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> メソッドは文字が大文字の場合に `true` を返します。

   `StartsWithUpper` は、<xref:System.String> クラスのメンバーであるかのように呼び出すことができる[拡張メソッド](../../csharp/programming-guide/classes-and-structs/extension-methods.md)として実装されます。

1. メニュー バーで、 **[ビルド]**  >  **[ソリューションのビルド]** を選択するか、<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>B</kbd> キーを押して、プロジェクトがエラーなくコンパイルされることを確認します。

## <a name="add-a-console-app-to-the-solution"></a>ソリューションにコンソール アプリを追加する

このクラス ライブラリを使用するコンソール アプリケーションを追加します。 アプリによって、ユーザーに文字列の入力が求められ、文字列が大文字で始まるかどうかが報告されます。

1. "ShowCase" という名前の新しい .NET コンソール アプリケーションをソリューションに追加します。

   1. **ソリューション エクスプローラー** で、ソリューションを右クリックし、 **[追加]**  >  **[新しいプロジェクト]** の順に選択します。

   1. **[新しいプロジェクトの追加]** ページで、検索ボックスに「**コンソール**」と入力します。 言語の一覧から **[C#]** または **[Visual Basic]** を選択し、次に、プラットフォームの一覧から **[すべてのプラットフォーム]** を選択します。

   1. **[コンソール アプリケーション]** テンプレートを選んでから、 **[次へ]** を選択します。

   1. **[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「**ShowCase**」と入力します。 **[次へ]** を選びます。

   1. **[追加情報]** ページで、 **[ターゲット フレームワーク]** ボックスの **[.NET 5.0 (Current)]** を選択します。 次に、 **[作成]** を選択します。

1. *Program.cs* または *Program.vb* ファイルのコード ウィンドウで、すべてのコードを次のコードに置き換えます。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   このコードでは、`row` 変数を使って、コンソール ウィンドウに書き込まれるデータの行数のカウントを維持します。 これが 25 以上になると、コードによってコンソール ウィンドウがクリアされ、ユーザーにメッセージが表示されます。

   プログラムは、ユーザーに文字列の入力を要求し、 文字列が大文字で始まるかどうかを示します。 ユーザーが文字列を入力せずに <kbd>Enter</kbd> キーを押すと、アプリケーションが終了し、コンソール ウィンドウが閉じます。

## <a name="add-a-project-reference"></a>プロジェクト参照を追加する

最初は、新しいコンソール アプリ プロジェクトにクラス ライブラリへのアクセス権はありません。 クラス ライブラリでメソッドを呼び出せるようにするには、クラス ライブラリ プロジェクトへのプロジェクト参照を作成します。

1. **ソリューション エクスプローラー** で、`ShowCase` プロジェクトの **[依存関係]** ノードを右クリックして、 **[プロジェクト参照の追加]** を選びます。

   :::image type="content" source="media/library-with-visual-studio/add-reference-context-menu.png" alt-text="Visual Studio の [参照の追加] コンテキスト メニュー":::

1. **[参照マネージャー]** ダイアログ ボックスで、 **[StringLibrary]** プロジェクトを選び、 **[OK]** を選びます。

   :::image type="content" source="media/library-with-visual-studio/manage-project-references.png" alt-text="StringLibrary が選択された [参照マネージャー] ダイアログ":::

## <a name="run-the-app"></a>アプリを実行する

1. **ソリューション エクスプローラー** で、**ShowCase** プロジェクトを右クリックして、コンテキスト メニューで **[スタートアップ プロジェクトに設定]** を選びます。

   :::image type="content" source="media/library-with-visual-studio/set-startup-project-context-menu.png" alt-text="スタートアップ プロジェクトを設定する Visual Studio プロジェクトのコンテキスト メニュー":::

1. <kbd>Ctrl</kbd>+<kbd>F5</kbd> キーを押して、デバッグなしでプログラムをコンパイルして実行します。

   :::image type="content" source="media/library-with-visual-studio/visual-studio-project-toolbar.png" alt-text="[デバッグ] ボタンを示している Visual Studio プロジェクトのツールバー":::

1. 文字列を入力して <kbd>Enter</kbd> キーを押してプログラムを実行し、<kbd>Enter</kbd> キーを押して終了します。

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="ShowCase が実行されているコンソール ウィンドウ":::

## <a name="additional-resources"></a>その他の技術情報

* [.NET CLI を使用してライブラリを開発する](libraries.md)
* [.NET Standard のバージョンとそれらでサポートされているプラットフォーム](../../standard/net-standard.md)。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、クラス ライブラリを作成しました。 次のチュートリアルでは、そのクラス ライブラリを単体テストする方法について説明します。

> [!div class="nextstepaction"]
> [Visual Studio を使用して .NET クラス ライブラリを単体テストする](testing-library-with-visual-studio.md)

または、自動化された単体テストをスキップし、NuGet パッケージを作成してそのライブラリを共有する方法を学習することもできます。

> [!div class="nextstepaction"]
> [Visual Studio を使用した、パッケージの作成と公開](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

または、コンソール アプリを公開する方法を学習することもできます。 このチュートリアルで作成したソリューションからそのコンソール アプリを発行すると、それに付属するクラス ライブラリは *.dll* ファイルとなります。

> [!div class="nextstepaction"]
> [Visual Studio を使用して .NET コンソール アプリケーションを発行する](publishing-with-visual-studio.md)
