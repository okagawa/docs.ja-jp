---
title: Visual Studio Code を使用して .NET クラス ライブラリを作成する
description: Visual Studio Code を使用して .NET クラス ライブラリを作成する方法について学習します。
ms.date: 11/18/2020
ms.openlocfilehash: 4473163b76060623b364d7dabf7366c3575e3dcd
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599500"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-code"></a>チュートリアル: Visual Studio Code を使用して .NET クラス ライブラリを作成する

このチュートリアルでは、1 つの文字列処理メソッドを含む簡単なユーティリティ ライブラリを作成します。

"*クラス ライブラリ*" は、アプリケーションから呼び出される型とメソッドを定義します。 ライブラリのターゲットが .NET Standard 2.0 である場合は、.NET Standard 2.0 をサポートする任意の .NET 実装 (.NET Framework を含む) で呼び出すことができます。 ライブラリのターゲットが .NET 5 である場合は、.NET 5 をターゲットとする任意のアプリケーションで呼び出すことができます。 このチュートリアルでは、.NET 5 をターゲットとする方法を示します。

クラス ライブラリを作成する場合は、サードパーティのコンポーネントとして、あるいは 1 つまたは複数のアプリケーションにバンドルされたコンポーネントとして配布することができます。

## <a name="prerequisites"></a>必須コンポーネント

1. [C# 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)がインストールされている [Visual Studio Code](https://code.visualstudio.com/)。 Visual Studio Code に拡張機能をインストールする方法については、[VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) を参照してください。
2. [.NET 5.0 SDK 以降](https://dotnet.microsoft.com/download)

## <a name="create-a-solution"></a>ソリューションを作成する

まず、クラス ライブラリ プロジェクトを配置する空のソリューションを作成します。 ソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。 さらに関連するプロジェクトを同じソリューションに追加します。

1. Visual Studio Code を開始します。

1. メイン メニューから **[ファイル]**  >  **[フォルダーを開く]** (macOS では **[開く...]** ) の順に選択します

1. **[フォルダーを開く]** ダイアログで、*ClassLibraryProjects* フォルダーを作成し、 **[フォルダーの選択]** (macOS では **[開く]** ) をクリックします。

1. メイン メニューで **[表示]**  >  **[ターミナル]** の順に選択して、Visual Studio Code で **ターミナル** を開きます。

   コマンド プロンプトで *ClassLibraryProjects* フォルダーが表示され、**ターミナル** が開きます。

1. **ターミナル** で、次のコマンドを入力します。

   ```dotnetcli
   dotnet new sln
   ```

   ターミナルには次の例のような出力があります。

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a>クラス ライブラリ プロジェクトを作成する

"StringLibrary" という名前の新しい .NET クラス ライブラリ プロジェクトをソリューションに追加します。

1. 次のコマンドをターミナルで実行して、ライブラリ プロジェクトを作成します。

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   `-o` コマンドまたは `--output` コマンドによって、生成された出力を配置する場所が指定されます。

   ターミナルには次の例のような出力があります。

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj (in 328 ms).
   Restore succeeded.
   ```

1. 次のコマンドを実行して、ライブラリ プロジェクトをソリューションに追加します。

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   ターミナルには次の例のような出力があります。

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. 確実にライブラリのターゲットが .NET 5 になっていることを確かめます。 **エクスプローラー** で、*StringLibrary/StringLibrary .csproj* を開きます。

   `TargetFramework` 要素に、プロジェクトのターゲットが .NET 5.0 であることが示されています。

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>net5.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. *Class1.cs* を開き、このコードを次のものと置き換えます。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   クラス ライブラリ `UtilityLibraries.StringLibrary` には、`StartsWithUpper` という名前のメソッドが含まれています。 このメソッドによって、現在の文字列のインスタンスが大文字で始まるかどうかを示す <xref:System.Boolean> 値が返されます。 Unicode 規格では、大文字と小文字が区別されます。 <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> メソッドは文字が大文字の場合に `true` を返します。

1. ファイルを保存します。

1. 次のコマンドを実行してソリューションをビルドし、エラーなしでプロジェクトがコンパイルされることを確認します。

   ```dotnetcli
   dotnet build
   ```

   ターミナルには次の例のような出力があります。

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\net5.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a>ソリューションにコンソール アプリを追加する

このクラス ライブラリを使用するコンソール アプリケーションを追加します。 アプリによって、ユーザーに文字列の入力が求められ、文字列が大文字で始まるかどうかが報告されます。

1. 次のコマンドをターミナルで実行して、コンソール アプリ プロジェクトを作成します。

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   ターミナルには次の例のような出力があります。

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj (in 210 ms).
   Restore succeeded.
   ```

1. 次のコマンドを実行して、ソリューションにコンソール アプリ プロジェクトを追加します。

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   ターミナルには次の例のような出力があります。

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. *ShowCase/Program.cs* を開き、すべてのコードを次のコードに置き換えます。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   このコードでは、`row` 変数を使って、コンソール ウィンドウに書き込まれるデータの行数のカウントを維持します。 これが 25 以上になると、コードによってコンソール ウィンドウがクリアされ、ユーザーにメッセージが表示されます。

   プログラムは、ユーザーに文字列の入力を要求し、 文字列が大文字で始まるかどうかを示します。 ユーザーが文字列を入力せずに <kbd>Enter</kbd> キーを押すと、アプリケーションが終了し、コンソール ウィンドウが閉じます。

1. 変更内容を保存します。

## <a name="add-a-project-reference"></a>プロジェクト参照を追加する

最初は、新しいコンソール アプリ プロジェクトにクラス ライブラリへのアクセス権はありません。 クラス ライブラリでメソッドを呼び出せるようにするには、クラス ライブラリ プロジェクトへのプロジェクト参照を作成します。

1. 次のコマンドを実行します。

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   ターミナルには次の例のような出力があります。

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a>アプリを実行する

1. ターミナルで次のコマンドを実行します。

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. 文字列を入力して <kbd>Enter</kbd> キーを押してプログラムを実行し、<kbd>Enter</kbd> キーを押して終了します。

   ターミナルには次の例のような出力があります。

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a>その他の技術情報

* [.NET CLI を使用してライブラリを開発する](libraries.md)
* [.NET Standard のバージョンとそれらでサポートされているプラットフォーム](../../standard/net-standard.md)。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、ソリューションを作成し、ライブラリ プロジェクトを追加し、ライブラリを使用するコンソール アプリ プロジェクトを追加しました。 次のチュートリアルでは、ソリューションに単体テスト プロジェクトを追加します。

> [!div class="nextstepaction"]
> [Visual Studio Code を使用して .NET で .NET クラス ライブラリをテストする](testing-library-with-visual-studio-code.md)
