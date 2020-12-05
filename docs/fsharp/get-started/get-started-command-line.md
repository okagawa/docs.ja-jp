---
title: 'コマンドラインツールを使用した F # の概要'
description: '任意のオペレーティングシステム (Windows、macOS、または Linux) で .NET Core CLI を使用して、F # でシンプルなマルチプロジェクトソリューションを構築する方法について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: f890e31fe8c665874dc3034aebfae32e38b9031a
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739916"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>.NET Core CLI で F # を使ってみる

この記事では、.NET Core CLI を使用して、任意のオペレーティングシステム (Windows、macOS、または Linux) で F # を使用する方法について説明します。 コンソールアプリケーションによって呼び出されるクラスライブラリを使用して、複数のプロジェクトから成るソリューションを構築します。

## <a name="prerequisites"></a>前提条件

まず、最新の [.NET Core SDK](https://dotnet.microsoft.com/download)をインストールする必要があります。

この記事では、コマンドラインの使用方法を理解し、適切なテキストエディターを使用することを前提としています。 まだ使用していない場合は、F # のテキストエディターとして [Visual Studio Code](get-started-vscode.md) が最適なオプションです。

## <a name="build-a-simple-multi-project-solution"></a>単純な複数プロジェクトソリューションの構築

コマンドプロンプト/ターミナルを開き、 [dotnet new](../../core/tools/dotnet-new.md) コマンドを使用して、という名前の新しいソリューションファイルを作成し `FSNetCore` ます。

```dotnetcli
dotnet new sln -o FSNetCore
```

前のコマンドを実行すると、次のディレクトリ構造が生成されます。

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>クラスライブラリを記述する

ディレクトリを *Fsnetcore* に変更します。

コマンドを使用して `dotnet new` 、"ライブラリ" という名前の **src** フォルダーにクラスライブラリプロジェクトを作成します。

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

前のコマンドを実行すると、次のディレクトリ構造が生成されます。

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

の内容を `Library.fs` 次のコードに置き換えます。

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    let json = JsonConvert.SerializeObject(value)
    $"I used to be {value} but now I'm {json} thanks to JSON.NET!"
```

NuGet パッケージの Newtonsoft.Jsをライブラリプロジェクトに追加します。

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

`Library` `FSNetCore` [Dotnet sln add](../../core/tools/dotnet-sln.md)コマンドを使用して、ソリューションにプロジェクトを追加します。

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

を実行し `dotnet build` てプロジェクトをビルドします。 未解決の依存関係は、ビルド時に復元されます。

### <a name="write-a-console-application-that-consumes-the-class-library"></a>クラスライブラリを使用するコンソールアプリケーションを作成する

コマンドを使用して、 `dotnet new` App という名前の **src** フォルダーにコンソールアプリケーションを作成します。

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

前のコマンドを実行すると、次のディレクトリ構造が生成されます。

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

`Program.fs` ファイルの内容を次のコードに置き換えます。

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    for arg in argv do
        let value = getJsonNetJson arg
        printfn $"{value}"

    0 // return an integer exit code
```

`Library` [Dotnet add reference](../../core/tools/dotnet-add-reference.md)を使用して、プロジェクトへの参照を追加します。

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

`App` `FSNetCore` 次のコマンドを使用して、ソリューションにプロジェクトを追加し `dotnet sln add` ます。

```dotnetcli
dotnet sln add src/App/App.fsproj
```

NuGet の依存関係を復元 `dotnet restore` し、を実行して `dotnet build` プロジェクトをビルドします。

コンソールプロジェクトにディレクトリを変更 `src/App` し、引数としてを渡してプロジェクトを実行し `Hello World` ます。

```dotnetcli
cd src/App
dotnet run Hello World
```

次のような結果が表示されます。

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>次のステップ

次に、F # のさまざまな機能の詳細については、 [f # のツアー](../tour.md) をご覧ください。
