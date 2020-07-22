---
title: '方法: タスクとその子を取り消す'
description: .NET でタスクとその子を取り消す方法の例を参照します。 この例では、取り消し可能なタスクの作成から、タスクが取り消されたことを知らせる通知までの手順を説明しています。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: 66daf00680b65aace1ce6367761e3ed81596d33b
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662681"
---
# <a name="how-to-cancel-a-task-and-its-children"></a>方法: タスクとその子を取り消す
以下の例では、次のタスクを実行する方法を説明します。  
  
1. 取り消すことができるタスクを作成し、開始します。  
  
2. キャンセル トークンをユーザー デリゲートに渡し、必要に応じてタスク インスタンスにも渡します。  
  
3. ユーザー デリゲート内のキャンセル要求を確認し、これに応答します。  
  
4. 必要に応じて、タスクが取り消された呼び出し元のスレッドを確認します。  
  
 呼び出し元のスレッドは、タスクを強制終了せず、キャンセルが要求されたことを通知するだけです。 タスクが既に実行中である場合、ユーザー デリゲートが要求を確認して適切に応答します。 タスクを実行する前にキャンセルが要求された場合、ユーザー デリゲートは実行されず、タスク オブジェクトは Canceled 状態に遷移します。  
  
## <a name="example"></a>例  
 次の例は、キャンセル要求に応答して <xref:System.Threading.Tasks.Task> およびその子を終了する方法を示しています。 また、ユーザー デリゲートが <xref:System.Threading.Tasks.TaskCanceledException> をスローして終了した場合、タスクの終了を待つために、呼び出し元スレッドが必要に応じて <xref:System.Threading.Tasks.Task.Wait%2A> メソッドまたは <xref:System.Threading.Tasks.Task.WaitAll%2A> メソッドを使用できることも示しています。 この例では `try/catch` ブロックを使用して、呼び出し元スレッドで例外を処理する必要があります。  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> クラスは、<xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> の型および <xref:System.Threading.CancellationToken?displayProperty=nameWithType> の型に基づくキャンセル モデルに完全に統合されています。 詳細については、「[マネージド スレッドのキャンセル](../threading/cancellation-in-managed-threads.md)」と「[タスクのキャンセル](task-cancellation.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [タスク ベースの非同期プログラミング](task-based-asynchronous-programming.md)
- [アタッチされた子タスクとデタッチされた子タスク](attached-and-detached-child-tasks.md)
- [PLINQ および TPL のラムダ式](lambda-expressions-in-plinq-and-tpl.md)
