---
title: dotnet-trace ツール - .NET Core
description: dotnet-trace コマンドライン ツールのインストールおよび使用。
ms.date: 11/21/2019
ms.openlocfilehash: d4175ccad785b21f860044a4fd5d691624ec495e
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507229"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>dotnet-trace パフォーマンス分析ユーティリティ

**この記事の対象:** ✔️ .NET Core 3.0 SDK 以降のバージョン

## <a name="install-dotnet-trace"></a>dotnet-trace をインストールする

[dotnet tool install](../tools/dotnet-tool-install.md) コマンドで `dotnet-trace` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-trace)をインストールします。

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>構文

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>説明

`dotnet-trace` ツール:

* クロスプラットフォーム .NET Core ツールです。
* ネイティブ プロファイラーなしで実行中のプロセスの .NET Core トレースを回収できます。
* .NET Core ランタイムのクロスプラットフォームの `EventPipe` テクノロジを中心に構築されています。
* Windows、Linux または macOS でも同じエクスペリエンスを提供します。

## <a name="options"></a>オプション

- **`-h|--help`**

  コマンド ライン ヘルプを表示します。

- **`--version`**

  dotnet-trace ユーティリティのバージョンを表示します。

## <a name="commands"></a>コマンド

| コマンド                                                   |
|-----------------------------------------------------------|
| [dotnet-trace collect](#dotnet-trace-collect)             |
| [dotnet-trace convert](#dotnet-trace-convert)             |
| [dotnet-trace ps](#dotnet-trace-ps)                       |
| [dotnet-trace list-profiles](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a>dotnet-trace collect

実行中のプロセスから診断トレースを収集します。

### <a name="synopsis"></a>構文

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a>オプション

- **`--buffersize <size>`**

  メモリ内の循環バッファーのサイズをメガバイトに設定します。 既定は 256 MB です。

- **`--clreventlevel <clreventlevel>`**

  生成される CLR イベントの詳細度。

- **`--clrevents <clrevents>`**

  生成する CLR ランタイム イベントの一覧。

- **`--format {Chromium|NetTrace|Speedscope}`**

  トレース ファイルの出力の変換形式を設定します。 既定値は、`NetTrace` です。

- **`-n, --name <name>`**

  トレースを収集するプロセスの名前。

- **`-o|--output <trace-file-path>`**

  収集されたトレース データの出力パス。 指定しない場合の既定値は `trace.nettrace` です。

- **`-p|--process-id <PID>`**

  トレースを収集するプロセス ID。

- **`--profile <profile-name>`**

  共通のトレース シナリオを簡潔に指定できるようにする、事前定義されたプロバイダーの名前付き構成のセット。

- **`--providers <list-of-comma-separated-providers>`**

  有効にする `EventPipe` プロバイダーのコンマ区切りのリスト。 これらのプロバイダーは、`--profile <profile-name>` で示されている任意のプロバイダーを補完します。 特定のプロバイダーに不整合がある場合、この構成がプロファイルの暗黙的な構成に優先されます。

  プロバイダーの一覧の形式は、次のとおりです。

  - `Provider[,Provider]`
  - `Provider` は、`KnownProviderName[:Flags[:Level][:KeyValueArgs]]` という形式です。
  - `KeyValueArgs` は、`[key1=value1][;key2=value2]` という形式です。

- **`-- <command>` (.NET 5.0 のみを実行しているターゲット アプリケーションの場合)**

  ユーザーは、コレクション構成パラメーターの後にまず `--`、次にコマンドを追加すれば、5.0 以降のランタイムで .NET アプリケーションを起動することができます。 これは、起動時のパフォーマンスの問題やアセンブリ ローダーおよびバインダーのエラーなど、プロセスの早い段階で発生する問題を診断するのに役立つ場合があります。

  > [!NOTE]
  > このオプションを使用すると、ツールに返信する最初の .NET 5.0 プロセスが監視されます。つまり、ご利用のコマンドで複数の .NET アプリケーションが起動される場合、収集されるのは最初のアプリのみとなります。 このため、このオプションについては、自己完結型アプリケーションに対して使用するか、または `dotnet exec <app.dll>` オプションを使用することをお勧めします。

## <a name="dotnet-trace-convert"></a>dotnet-trace convert

`nettrace` トレースを、別のトレース分析ツールで使用するために、別の形式に変換します。

### <a name="synopsis"></a>構文

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a>引数

- **`<input-filename>`**

  変換する入力トレース ファイル。 既定は *trace.nettrace* です。

### <a name="options"></a>オプション

- **`--format <Chromium|NetTrace|Speedscope>`**

  トレース ファイルの出力の変換形式を設定します。

- **`-o|--output <output-filename>`**

  出力ファイルの名前。 ターゲットの形式の拡張子が追加されます。

## <a name="dotnet-trace-ps"></a>dotnet-trace ps

 トレースを収集できる dotnet プロセスを一覧表示します。

### <a name="synopsis"></a>構文

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet-trace list-profiles

各プロファイルに含まれるプロバイダーとフィルターの記述と共に、事前に構築されているトレースのプロファイルを一覧表示します。

### <a name="synopsis"></a>構文

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>dotnet-trace を使用してトレースを収集する

`dotnet-trace` を使用してトレースを収集するには:

- トレースを収集する .NET Core アプリケーションのプロセス識別子 (PID) を取得します。

  - Windows で、タスク マネージャーや、たとえば、`tasklist` コマンドを使用できます。
  - Linux の場合、たとえば、`ps` コマンドを使用できます。
  - [dotnet-trace ps](#dotnet-trace-ps)

- 次のコマンドを実行します。

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  上のコマンドを実行すると、次のような出力が生成されます。

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- `<Enter>` キーを押すと、コレクションが停止します。 `dotnet-trace` では、*trace.nettrace* ファイルにイベントをログ記録する作業が完了します。

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a>子アプリケーションを起動し、そのスタートアップからトレースを dotnet-trace を使用して収集します

注:これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。

場合によっては、プロセスのトレースをそのスタートアップから収集すると便利なことがあります。 .NET 5.0 以降を実行しているアプリでは、dotnet-trace を使用してこれを行うことができます。

これを使用すると、コマンドライン引数として `arg1` と `arg2` を含む `hello.exe` が起動され、ランタイム スタートアップからトレースが収集されます。

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

上のコマンドを実行すると、次のような出力が生成されます。

```console
No profile or providers specified, defaulting to trace profile 'cpu-sampling'

Provider Name                           Keywords            Level               Enabled By
Microsoft-DotNETCore-SampleProfiler     0x0000F00000000000  Informational(4)    --profile
Microsoft-Windows-DotNETRuntime         0x00000014C14FCCBD  Informational(4)    --profile

Process        : E:\temp\gcperfsim\bin\Debug\net5.0\gcperfsim.exe
Output File    : E:\temp\gcperfsim\trace.nettrace


[00:00:00:05]   Recording trace 122.244  (KB)
Press <Enter> or <Ctrl+C> to exit...
```

トレースの収集を停止するには、`<Enter>` または `<Ctrl + C>` キーを押します。 この操作を行うと、`hello.exe` も終了します。

> [!NOTE]
> dotnet-trace を介して `hello.exe` を起動すると、その入力/出力がリダイレクトされ、その stdin/stdout とやりとりができなくなります。
> CTRL + C または SIGTERM を介してツールを終了すると、ツールと子プロセスの両方が安全に終了します。
> ツールの前に子プロセスが終了すると、ツールも終了し、トレースを安全に表示できるようになります。

## <a name="view-the-trace-captured-from-dotnet-trace"></a>dotnet-trace からキャプチャされたトレースを表示する

Windows の場合、 *.nettrace* ファイルを [PerfView](https://github.com/microsoft/perfview) で表示し、分析できます。他のプラットフォームで収集されたトレースについては、トレース ファイルを Windows コンピューターに移動し、PerfView で表示できます。

Linux の場合、`dotnet-trace` の出力形式を `speedscope` に変更することでトレースを表示できます。 出力ファイル形式は `-f|--format` オプションで変更できます。`-f speedscope` により、`dotnet-trace` で `speedscope` ファイルが生成されます。 `nettrace` (既定のオプション) か `speedscope` を選択できます。 `Speedscope` ファイルは <https://www.speedscope.app> で開くことができます。

> [!NOTE]
> .NET Core ランタイムにより、`nettrace` 形式でトレースが生成されます。 トレースの完了後、トレースは speedscope に変換されます (指定されている場合)。 変換によってはデータが失われる場合もあるため、元の `nettrace` ファイルが変換されたファイルの横に保持されます。

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>dotnet-trace を使用して経時的なカウンター値を収集する

`dotnet-trace` でできること:

* パフォーマンスで左右される環境で基本的な正常性監視を行うには `EventCounter` を使用します。 たとえば、運用環境です。
* リアルタイムで表示する必要がないようにトレースを収集します。

たとえば、実行時のパフォーマンス カウンター値を収集するには、次のコマンドを使用します。

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

先のコマンドでは、正常性の簡易監視を 1 秒ごとに報告するようにランタイム カウンターに命令します。 `EventCounterIntervalSec=1` の値を (60 など) 大きい値に置き換えた場合、カウンター データの細分性の詳細度がより低いトレースをより少数収集できるようになります。

次のコマンドでは、先のコマンドよりオーバーヘッドとトレース サイズが少なくなります。

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

上のコマンドでは、ランタイム イベントとマネージド スタック プロファイラーが無効になります。

## <a name="net-providers"></a>.NET プロバイダー

.NET Core ランタイムでは、次の .NET プロバイダーがサポートされています。 .NET Core では、`Event Tracing for Windows (ETW)` と `EventPipe` トレースの有効化に、いずれも同じキーワードを使用しています。

| プロバイダー名                            | 情報 |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [ランタイム プロバイダー](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[CLR ランタイム キーワード](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [ランダウン プロバイダー](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[CLR ランダウン キーワード](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | サンプル プロファイラーを有効にします。 |
