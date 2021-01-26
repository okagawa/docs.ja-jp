---
title: 完了時の非同期タスクの処理
description: この例では、C# で Task.WhenAny を使用して複数のタスクを開始し、その結果を開始の順番で処理するのではなく、完了時に処理する方法を示します。
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 4cdd35af900863895911ea5c2c9772af362951ec
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615972"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a>完了時の非同期タスクの処理 (C#)

<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> を使用すると、複数のタスクを、開始された順番に処理するのでなく、同時に開始して完了するごとに 1 つずつ処理できます。

クエリを使用して、タスクのコレクションを作成する例を次に示します。 各タスクは、指定された Web サイトのコンテンツをダウンロードします。 while ループの各反復で、待機されている <xref:System.Threading.Tasks.Task.WhenAny%2A> への呼び出しは、最初にダウンロードを終了するタスクのコレクションにあるタスクを返します。 タスクはコレクションから削除され、処理されます。 ループは、コレクションのタスクがなくなるまで繰り返されます。

## <a name="create-example-application"></a>サンプル アプリケーションの作成

新しい .NET Core コンソール アプリケーションを作成します。 [dotnet new console](../../../../core/tools/dotnet-new.md#console) コマンドを使用するか、[Visual Studio](/visualstudio/install/install-visual-studio) を使用して作成できます。 任意のコード エディターで *Program.cs* ファイルを開きます。

### <a name="replace-using-statements"></a>using ステートメントの置換

既存の using ステートメントを次の宣言に置き換えます。

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a>フィールドを追加する

`Program` クラスの定義に、次の 2 つのフィールドを追加します。

```csharp
static readonly HttpClient s_client = new HttpClient
{
    MaxResponseContentBufferSize = 1_000_000
};

static readonly IEnumerable<string> s_urlList = new string[]
{
    "https://docs.microsoft.com",
    "https://docs.microsoft.com/aspnet/core",
    "https://docs.microsoft.com/azure",
    "https://docs.microsoft.com/azure/devops",
    "https://docs.microsoft.com/dotnet",
    "https://docs.microsoft.com/dynamics365",
    "https://docs.microsoft.com/education",
    "https://docs.microsoft.com/enterprise-mobility-security",
    "https://docs.microsoft.com/gaming",
    "https://docs.microsoft.com/graph",
    "https://docs.microsoft.com/microsoft-365",
    "https://docs.microsoft.com/office",
    "https://docs.microsoft.com/powershell",
    "https://docs.microsoft.com/sql",
    "https://docs.microsoft.com/surface",
    "https://docs.microsoft.com/system-center",
    "https://docs.microsoft.com/visualstudio",
    "https://docs.microsoft.com/windows",
    "https://docs.microsoft.com/xamarin"
};
```

`HttpClient` では、HTTP 要求を送信して HTTP 応答を受信する機能が公開されます。 `s_urlList` には、このアプリケーションで処理を計画するすべての URL が格納されます。

## <a name="update-application-entry-point"></a>アプリケーション エントリ ポイントの更新

コンソール アプリケーションのメイン エントリ ポイントは、`Main` メソッドです。 既存のメソッドを以下に置き換えます。

```csharp
static Task Main() => SumPageSizesAsync();
```

更新した `Main` メソッドは、[async main](../../../whats-new/csharp-7.md#async-main) と見なされるようになります。これにより、実行可能ファイルへの非同期エントリ ポイントが可能になります。 これは、`SumPageSizesAsync` の呼び出しを表しています。

## <a name="create-the-asynchronous-sum-page-sizes-method"></a>非同期の合計ページ サイズ メソッドの作成

`Main` メソッドの下に、`SumPageSizesAsync` メソッドを追加します。

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in s_urlList
        select ProcessUrlAsync(url, s_client);

    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;
    while (downloadTasks.Any())
    {
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);
        downloadTasks.Remove(finishedTask);
        total += await finishedTask;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

このメソッドを開始するには、<xref:System.Diagnostics.Stopwatch> をインスタンス化して開始します。 それには、実行時にタスクのコレクションを作成するクエリが含まれます。 次のコードの `ProcessUrlAsync` への各呼び出しは、`TResult` が整数である <xref:System.Threading.Tasks.Task%601> を返します。

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

LINQ での[遅延実行](../../../../standard/linq/deferred-execution-example.md)のため、各タスクを開始するには <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> を呼び出します。

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

`while` ループでは、コレクション内の各タスクに対して次の手順が実行されます。

1. `WhenAny` への呼び出しを待機し、コレクション内で最初にダウンロードが終了したタスクを識別します。

    ```csharp
    Task<int> finishedTask = await Task.WhenAny(downloadTasks);
    ```

1. コレクションからそのタスクを削除します。

    ```csharp
    downloadTasks.Remove(finishedTask);
    ```

1. `finishedTask` への呼び出しから返される、`ProcessUrlAsync` を待機します。 `finishedTask` 変数は <xref:System.Threading.Tasks.Task%601> が整数である `TResult` です。 次の例に示すように、タスクは既に完了していますが、ダウンロードした Web サイトの長さの取得を待機します。 タスクが失敗した場合、`AggregateException` がスローされる <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> プロパティの読み取りとは異なり、`await` からは `AggregateException` に格納されている最初の子の例外がスローされます。

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a>プロセス メソッドの追加

`SumPageSizesAsync` メソッドの下に次の `ProcessUrlAsync` メソッドを追加します。

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

どの URL に対しても、このメソッドにより、提供される `client` インスタンスが使用され、応答が `byte[]` として取得されます。 URL と長さがコンソールに出力された後、長さが返されます。

ダウンロードされた長さが常に同じ順序では表示されないことを確認するために、プログラムを複数回実行します。

> [!CAUTION]
> ループで `WhenAny` を使って、例に示すように、いくつかのタスクを格納する問題を解決できます。 ただし、多数のタスクが処理する場合、他のアプローチがより効率的です。 詳細と例については、「[Processing Tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete)」 (完了したタスクを処理する) を参照してください。

## <a name="complete-example"></a>コード例全体

次のコードは、この例の *Program.cs* ファイルの完全なテキストです。

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a>関連項目

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Async および Await を使用した非同期プログラミング (C#)](index.md)
