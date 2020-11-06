---
title: スレッドの協調的な取り消し
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: 36de18e976401dd0cde878852c064aa982b8acde
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188498"
---
# <a name="canceling-threads-cooperatively"></a>スレッドの協調的な取り消し

.NET Framework 4 より前のバージョンの .NET には、開始されたスレッドを協調的に取り消す手段は組み込まれていませんでした。 ただし、.NET Framework 4 以降、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトや PLINQ クエリを取り消す場合と同様に、<xref:System.Threading.CancellationToken?displayProperty=nameWithType> を使用してスレッドを取り消すことができます。 <xref:System.Threading.Thread?displayProperty=nameWithType> クラスにはキャンセル トークンのサポートは組み込まれていませんが、<xref:System.Threading.ParameterizedThreadStart> デリゲートを受け取る <xref:System.Threading.Thread> コンストラクターを使用して、トークンをスレッド プロシージャに渡すことができます。 この方法を次の例に示します。  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>参照

- [スレッドの使用とスレッド処理](using-threads-and-threading.md)
