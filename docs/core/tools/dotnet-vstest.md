---
title: dotnet vstest コマンド
description: dotnet vstest コマンドは、プロジェクトとそのすべての依存関係をビルドします。
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975395"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン

> [!IMPORTANT]
> `dotnet vstest` コマンドに取って代わりのが `dotnet test` であり、これでアセンブリを実行できます。 [`dotnet test`](dotnet-test.md) をご覧ください。

## <a name="name"></a>名前

`dotnet-vstest` - 指定されたアセンブリからテストを実行します。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a>説明

`dotnet-vstest` コマンドでは、`VSTest.Console` コマンド ライン アプリケーションが実行されて、自動単体テストが実行されます。

## <a name="arguments"></a>引数

- **`TEST_FILE_NAMES`**

  指定されたアセンブリからテストを実行します。 複数のテスト アセンブリ名を指定するときは、空白で区切ります。 ワイルドカードを利用できます。

## <a name="options"></a>オプション

- **`--Blame`**

  変更履歴モードでテストを実行します。 このオプションは、テスト ホストのクラッシュを引き起こす問題のあるテストを分離するのに役立ちます。 これは、現在のディレクトリ内に出力ファイルを *Sequence.xml* として作成します。このファイルは、クラッシュ前にテストの実行順序をキャプチャします。

- **`--Diag <PATH_TO_LOG_FILE>`**

  テスト プラットフォームの詳細ログを有効にします。 指定されたファイルにログが書き込まれます。

- **`--Framework <FRAMEWORK>`**

  テストの実行に使用する対象の .NET Framework バージョンです。 有効な値の例としては、`.NETFramework,Version=v4.6` や `.NETCoreApp,Version=v1.0` などがあります。 サポートされるその他の値は、`Framework40`、`Framework45`、`FrameworkCore10`、および `FrameworkUap10` です。

- **`--InIsolation`**

  分離プロセスでテストを実行します。 これにより、テストでエラーが発生しても *vstest.console.exe* プロセスが停止することは少なくなりますが、テストの実行速度は低下する可能性があります。

- **`-lt|--ListTests <FILE_NAME>`**

  指定されたテスト コンテナーから探索されたテストをすべて一覧表示します。

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  テスト結果のロガーを指定します。

  - Team Foundation Server にテスト結果を発行するには、次のように `TfsPublisher` ロガー プロバイダーを使用します。

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Visual Studio テスト結果ファイル (TRX) に結果のログを書き込むには、`trx` ロガー プロバイダーを使用します。 このように切り替えることで、テスト結果ディレクトリに指定のログ ファイル名でファイルが作成されます。 `LogFileName` が指定されていない場合は、テスト結果を保持するために一意のファイル名が作成されます。

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  テストを並列で実行します。 既定では、コンピューター上のすべての使用可能なコアを使用できます。 *runsettings* ファイルの `RunConfiguration` ノードの下に `MaxCpuCount` プロパティを設定して、明示的なコア数を指定します。

- **`--ParentProcessId <PROCESS_ID>`**

  現在のプロセスを起動する親プロセスのプロセス ID です。

- **`--Platform <PLATFORM_TYPE>`**

  テストの実行に使用する対象のプラットフォーム アーキテクチャです。 有効な値は `x86`、`x64`、`ARM` です。

- **`--Port <PORT>`**

  ソケット接続およびイベント メッセージの受信用のポートを指定します。

- **`--ResultsDirectory:<PATH>`**

  テスト結果ディレクトリが存在しない場合、指定されたパスに作成されます。

- **`--Settings <SETTINGS_FILE>`**

  テストの実行時に使用される設定です。

- **`--TestAdapterPath <PATH>`**

  テストの実行では、指定されたパス (存在する場合) からカスタム テスト アダプターを使用します。

- **`--TestCaseFilter <EXPRESSION>`**

  指定した式に一致するテストを実行します。 `<EXPRESSION>` の形式は `<property>Operator<value>[|&<EXPRESSION>]` です。この場合の演算子は `=`、`!=`、または `~` のいずれかになります。 演算子 `~` は 'contains' セマンティクスを持ち、`DisplayName` などの文字列プロパティに適用できます。 サブ式のグループ化には、かっこ `()` を使用します。 詳細については、[TestCase フィルター](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)に関するページを参照してください。

- **`--Tests <TEST_NAMES>`**

  指定した値に一致する名前のテストを実行します。 複数の値を指定するときは、コンマで区切ります。

- **`-?|--Help`**

  コマンドの短いヘルプを印刷します。

- **`@<file>`**

  応答ファイルを読み込んで、オプションを追加します。

- **`args`**

  アダプターに渡す追加の引数を指定します。 引数は `<n>=<v>` 形式の名前と値のペアとして指定されます。この場合の `<n>` は引数名、`<v>` は引数値です。 複数の引数を指定する場合は、空白で区切ります。

## <a name="examples"></a>使用例

*mytestproject.dll* でテストを実行します。

```dotnetcli
dotnet vstest mytestproject.dll
```

*mytestproject.dll* でテストを実行し、カスタム名を指定してカスタム フォルダーにエクスポートします。

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

*mytestproject.dll* と *myothertestproject.exe* でテストを実行します。

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

`TestMethod1` テストを実行する:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

`TestMethod1` および `TestMethod2` テストを実行する:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a>関連項目

- [VSTest.Console.exe のコマンド ライン オプション](/visualstudio/test/vstest-console-options)
