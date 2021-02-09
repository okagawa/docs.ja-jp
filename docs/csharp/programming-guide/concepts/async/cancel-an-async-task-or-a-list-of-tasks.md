---
title: タスクの一覧をキャンセルする (C#)
description: キャンセル トークンを使用して、タスクの一覧にキャンセル要求を通知する方法について説明します。
ms.date: 02/03/2021
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 532c61ab6499583620ba2ee5c710c58f7886f89d
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585742"
---
# <a name="cancel-a-list-of-tasks-c"></a>タスクの一覧をキャンセルする (C#)

非同期のコンソール アプリケーションは、終了まで待機しない場合にキャンセルすることができます。 このトピックの例に従うと、Web サイトの一覧のコンテンツをダウンロードするアプリケーションにキャンセルを追加できます。 各タスクに <xref:System.Threading.CancellationTokenSource> インスタンスを関連付けると、多くのタスクをキャンセルすることができます。 <kbd>Enter</kbd> キーを選択すると、完了していないすべてのタスクがキャンセルされます。

このチュートリアルの内容:

> [!div class="checklist"]
>
> - .NET コンソール アプリケーションの作成
> - キャンセルをサポートする非同期アプリケーションの作成
> - キャンセル通知のデモンストレーション

## <a name="prerequisites"></a>前提条件

このチュートリアルには、次のものが必要です。

- [.NET 5.0 以降の SDK](https://dotnet.microsoft.com/download/dotnet/5.0)
- 統合開発環境 (IDE)
  - [Visual Studio、Visual Studio Code、または Visual Studio for Mac をお勧めします](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a>サンプル アプリケーションの作成

新しい .NET Core コンソール アプリケーションを作成します。 [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) コマンドを使用するか、[Visual Studio](/visualstudio/install/install-visual-studio) から作成できます。 任意のコード エディターで *Program.cs* ファイルを開きます。

### <a name="replace-using-statements"></a>using ステートメントの置換

既存の using ステートメントを次の宣言に置き換えます。

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a>フィールドを追加する

`Program` クラス定義で、次の 3 つのフィールドを追加します。

```csharp
static readonly CancellationTokenSource s_cts = new CancellationTokenSource();

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

<xref:System.Threading.CancellationTokenSource> は、要求されるキャンセルを <xref:System.Threading.CancellationToken> に通知するために使用されます。 `HttpClient` では、HTTP 要求を送信して HTTP 応答を受信する機能が公開されます。 `s_urlList` には、このアプリケーションで処理を計画するすべての URL が格納されます。

## <a name="update-application-entry-point"></a>アプリケーション エントリ ポイントの更新

コンソール アプリケーションのメイン エントリ ポイントは、`Main` メソッドです。 既存のメソッドを以下に置き換えます。

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");
    Console.WriteLine("Press the ENTER key to cancel...\n");

    Task cancelTask = Task.Run(() =>
    {
        while (Console.ReadKey().Key != ConsoleKey.Enter)
        {
            Console.WriteLine("Press the ENTER key to cancel...");
        }

        Console.WriteLine("\nENTER key pressed: cancelling downloads.\n");
        s_cts.Cancel();
    });

    Task sumPageSizesTask = SumPageSizesAsync();

    await Task.WhenAny(new[] { cancelTask, sumPageSizesTask });

    Console.WriteLine("Application ending.");
}
```

更新した `Main` メソッドは、[async main](../../../whats-new/csharp-7.md#async-main) と見なされるようになります。これにより、実行可能ファイルへの非同期エントリ ポイントが可能になります。 いくつかの指示メッセージがコンソールに出力され、次に `cancelTask` という名前の <xref:System.Threading.Tasks.Task> インスタンスが宣言されます。これにより、コンソールのキー ストロークが読み取られるようになります。 <kbd>Enter</kbd> キーが押されると、<xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> の呼び出しが行われます。 これにより、キャンセルが通知されるようになります。 次に、`sumPageSizesTask` 変数が `SumPageSizesAsync` メソッドから割り当てられています。 両方のタスクは次に <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> に渡され、2 つのタスクのいずれかが完了したときに続行されるようになります。

## <a name="create-the-asynchronous-sum-page-sizes-method"></a>非同期の合計ページ サイズ メソッドの作成

`Main` メソッドの下に、`SumPageSizesAsync` メソッドを追加します。

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    int total = 0;
    foreach (string url in s_urlList)
    {
        int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
        total += contentLength;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

このメソッドを開始するには、<xref:System.Diagnostics.Stopwatch> をインスタンス化して開始します。 次に、`s_urlList` 内の各 URL をループし、`ProcessUrlAsync` を呼び出します。 反復処理のたびに、`s_cts.Token` が `ProcessUrlAsync` メソッドに渡され、コードから <xref:System.Threading.Tasks.Task%601> が返されます。`TResult` は整数です。

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a>プロセス メソッドの追加

`SumPageSizesAsync` メソッドの下に次の `ProcessUrlAsync` メソッドを追加します。

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync(token);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

どの URL に対しても、このメソッドにより、提供される `client` インスタンスが使用され、応答が `byte[]` として取得されます。 <xref:System.Threading.CancellationToken> インスタンスは、<xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> および <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> メソッドに渡されます。 `token` は、要求されるキャンセルの登録に使用されます。 URL と長さがコンソールに出力された後、長さが返されます。

### <a name="example-application-output"></a>アプリケーション出力の例

```console
Application started.
Press the ENTER key to cancel...

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663
https://docs.microsoft.com/dotnet                                67,452
https://docs.microsoft.com/dynamics365                           48,582
https://docs.microsoft.com/education                             22,924

ENTER key pressed: cancelling downloads.

Application ending.
```

## <a name="complete-example"></a>コード例全体

次のコードは、この例の *Program.cs* ファイルの完全なテキストです。

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a>関連項目

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [Async および Await を使用した非同期プログラミング (C#)](index.md)

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [指定した時間の経過後の非同期タスクのキャンセル (C#)](cancel-async-tasks-after-a-period-of-time.md)
