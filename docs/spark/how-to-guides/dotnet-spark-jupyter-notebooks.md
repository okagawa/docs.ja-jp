---
title: Jupyter Notebook を使用する
titleSuffix: .NET for Apache Spark
description: Jupyter Notebook、Jupyter Lab、Visual Studio Code (VS Code) などの対話型環境で .NET for Apache Spark を使用する
ms.author: luquinta
author: luisquintanilla
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc, how-to
ms.openlocfilehash: 9c0e713731b5e2ad742bdd257a99f9029f244363
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536113"
---
# <a name="use-net-for-apache-spark-in-jupyter-notebooks"></a>.NET for Apache Spark を Jupyter Notebook で使用する

この記事では、NET Interactive を使用して .NET for Apache Spark ジョブを Jupyter Notebook と Visual Studio Code (VS Code) で対話的に実行する方法について説明します。

## <a name="about-jupyter"></a>Jupyter について

[Jupyter](https://jupyter.org/) は、オープンソースのクロスプラットフォーム コンピューティング環境で、アプリケーションのプロトタイプ作成と開発を対話的に行う方法がユーザーに提供されます。 Jupyter Notebook、Jupyter Lab、VS Code などのさまざまなインターフェイスを介して、Jupyter と対話することができます。

.NET のコンテキストでは、.NET Core グローバル ツールである [.NET Interactive](https://github.com/dotnet/interactive) によって、Jupyter Notebook などの対話型コンピューティング環境に .NET コード (C# または F#) を記述するためのカーネルが提供されます。

## <a name="prerequisites"></a>前提条件

- [.NET Core 3.1 SDK](../../core/install/index.yml)
- [Apache Spark](https://spark.apache.org/downloads.html)
- [Apache Spark .NET Worker](https://github.com/dotnet/spark/releases)

.NET for Apache Spark 環境用に設定する方法の詳細については、[入門チュートリアル](../tutorials/get-started.md)を参照してください。

## <a name="prepare-environment"></a>環境を準備する

Jupyter Notebook を使用するには、2 つのことが必要です。

1. [.NET Interactive グローバル .NET ツール](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)をインストールします
1. `Microsoft.Spark` NuGet パッケージをダウンロードします。
    1. [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet パッケージ ページに移動します。

        > [!IMPORTANT]
        > 既定では、最新バージョンのパッケージがダウンロードされます。 **ダウンロードしたバージョンがご使用の Apache Spark .NET Worker と同じであることを確認します。**

    1. **[情報]** ウィンドウで、 **[パッケージのダウンロード]** を選択してパッケージの最新バージョンをダウンロードします。 パッケージの名前は、"*microsoft.spark.[パッケージのバージョン].nupkg*" のようなものになります。
    1. ダウンロードしたパッケージを解凍します。 解凍されたディレクトリには *jar* という名前のサブディレクトリが含まれているはずです。 パスは後で使用するため、メモしておいてください。

## <a name="start-net-for-apache-spark"></a>.NET for Apache Spark を開始する

次のコマンドを実行して、デバッグ モードで .NET for Apache Spark を開始します。 この `spark-submit` コマンドはプロセスを開始し、[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) からの接続を待機します。 使用している .NET for Apache Spark に対応するバージョンの `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` へのパスを必ず指定してください。

**Ubuntu**

```bash
spark-submit \
    --class org.apache.spark.deploy.dotnet.DotnetRunner \
    --master local \
    <path-to-microsoft-spark-jar> \
    debug
```

**Windows**

```cmd
spark-submit ^
    --class org.apache.spark.deploy.dotnet.DotnetRunner ^
    --master local ^
    <path-to-microsoft-spark-jar> ^
    debug
```

## <a name="create-a-notebook"></a>ノートブックを作成する

さまざまなインターフェイスを使用して、Jupyter とやり取りできます。 ブラウザーベースのインターフェイスの場合は、Jupyter Notebook または Jupyter Lab を使用します。 ローカル エディターを使用する場合は、VS Code を使用します。

### <a name="jupyter-notebooks--jupyter-lab"></a>Jupyter Notebooks と Jupyter Lab

1. 別のコマンド プロンプトで、次のいずれかのコマンドを使用して Jupyter Notebook または Jupyter Lab を開始します。

    **Jupyter Notebook**

    ```bash
    jupyter notebook
    ```

    **Jupyter Lab**

    ```bash
    jupyter lab
    ```

    これらのコマンドにより、Jupyter Notebook または Jupyter Lab インターフェイスを使用したブラウザー ウィンドウが起動されます。

1. ブラウザーで、新しいノートブックを作成します。

    **Jupyter Notebook**

    **[新規] > [.NET (C#)]** または **[新規] > [.NET (F#)]** を選択します

    **Jupyter Lab**

    ランチャー ウィンドウで、 **[.NET (C#)]** または **[.NET (F#)]** を選択します

### <a name="visual-studio-code-preview"></a>Visual Studio Code (プレビュー)

> [!IMPORTANT]
> VS Code で Jupyter Notebook を使用するには、次のものをインストールする必要があります。
>
>- [VS Code Insiders](https://code.visualstudio.com/insiders/)
>- [.NET Interactive Notebooks 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode)

1. VS Code を開きます。
1. **[表示] > [コマンド パレット]** でコマンド パレットを開きます。

    コマンド パレットが表示されたら、次のコマンドを入力して、新しい .NET Interactive ノートブックを作成します。

    ```text
    >.NET Interactive: Create new blank notebook
    ```

    または、 *.ipynb* 拡張機能を使用して既存の .NET Interactive ノートブックを開く場合は、次のコマンドを使用します。

    ```text
    >.NET Interactive: Open notebook
    ```

## <a name="initialize-a-spark-session"></a>Spark セッションを初期化する

1. ノートブックが開いたら、`Microsoft.Spark` NuGet パッケージをインストールします。 インストールするバージョンが .NET Worker と同じであることを確認します。

    ```text
    #r "nuget:Microsoft.Spark, 1.0.0"
    ```

1. 次の using ステートメントをノートブックに追加します。

    ```csharp
    using Microsoft.Spark.Sql;
    ```

1. ご自分の [SparkSession](xref:Microsoft.Spark.Sql.SparkSession) を初期化します。

    ```csharp
    var sparkSession =
    SparkSession
        .Builder()
        .AppName("dotnet-interactive-spark")
        .GetOrCreate();
    ```

ノートブックは次の図のようなものになります。 この例では VS Code を使用していますが、Jupyter Notebook と Jupyter Lab でも同じように見えます。

> [!div class="mx-imgBorder"]
![.NET for Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)

## <a name="next-steps"></a>次の手順

- [.NET for Apache Spark の概要](../tutorials/get-started.md)
- [.NET for Apache Spark と ML.NET を使用してセンチメントを予測する](../tutorials/ml-sentiment-analysis.md)
- .NET Interactive の詳細については、[.NET Interactive に関するドキュメント](https://github.com/dotnet/interactive/blob/main/docs/README.md)を参照してください。
