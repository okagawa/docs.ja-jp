---
title: 指定した時間の経過後の非同期タスクのキャンセル (C#)
description: 指定した期間内に完了していない、関連付けられたタスクのキャンセルをスケジュールする方法について説明します。
ms.date: 02/03/2021
ms.topic: tutorial
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 98c42a2df6153d668b99b6dec49ffe380293b205
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585378"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>指定した時間の経過後の非同期タスクのキャンセル (C#)

<xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> メソッドを使用すると、一定の時間が過ぎた後に非同期操作が完了するまで待たない場合に、キャンセルすることができます。 このメソッドは、`CancelAfter` 式によって指定された時間内に完了しない、関連付けられたタスクのキャンセルをスケジュールします。

この例は、[タスクの一覧のキャンセル (C#)](cancel-an-async-task-or-a-list-of-tasks.md)に関する記事で開発したコードに追加して、Web サイトの一覧をダウンロードしてそれぞれのコンテンツの長さを表示します。

このチュートリアルの内容:

> [!div class="checklist"]
>
> - 既存の .NET コンソール アプリケーションの更新
> - キャンセルのスケジュール

## <a name="prerequisites"></a>前提条件

このチュートリアルには、次のものが必要です。

- [タスクの一覧のキャンセル (C#)](cancel-an-async-task-or-a-list-of-tasks.md) のチュートリアルでアプリケーションを作成しておきます
- [.NET 5.0 以降の SDK](https://dotnet.microsoft.com/download/dotnet/5.0)
- 統合開発環境 (IDE)
  - [Visual Studio、Visual Studio Code、または Visual Studio for Mac をお勧めします](https://visualstudio.microsoft.com)

## <a name="update-application-entry-point"></a>アプリケーション エントリ ポイントの更新

既存の`Main` メソッドを以下に置き換えます。

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");

    try
    {
        s_cts.CancelAfter(3500);

        await SumPageSizesAsync();
    }
    catch (TaskCanceledException)
    {
        Console.WriteLine("\nTasks cancelled: timed out.\n");
    }
    finally
    {
        s_cts.Dispose();
    }

    Console.WriteLine("Application ending.");
}
```

更新された `Main` メソッドで、いくつかの指示メッセージがコンソールに書き込まれます。 [try catch](../../../language-reference/keywords/try-catch.md) 内で、<xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> を呼び出してキャンセルをスケジュールします。 これにより、一定の期間後にキャンセルが通知されます。

次に、`SumPageSizesAsync` メソッドが待機されます。 スケジュールされたキャンセルよりも、すべての URL の処理が早く行われると、アプリケーションは終了します。 ただし、すべての URL が処理される前にスケジュールされたキャンセルがトリガーされると、<xref:System.Threading.Tasks.TaskCanceledException> がスローされます。

### <a name="example-application-output"></a>アプリケーション出力の例

```console
Application started.

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663

Tasks cancelled: timed out.

Application ending.
```

## <a name="complete-example"></a>コード例全体

次のコードは、この例の *Program.cs* ファイルの完全なテキストです。

:::code language="csharp" source="snippets/cancel-tasks/cancel-task-after-period-of-time/Program.cs":::

## <a name="see-also"></a>関連項目

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [Async および Await を使用した非同期プログラミング (C#)](index.md)
- [タスクの一覧をキャンセルする (C#)](cancel-an-async-task-or-a-list-of-tasks.md)
