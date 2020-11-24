---
title: タスク並列ライブラリ (TPL)
description: .NET のアプリケーションに並列処理とコンカレンシーを追加するプロセスを簡略化するためのパブリック型と API のセットから成るタスク並列ライブラリ (TPL) について確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
ms.openlocfilehash: 5c26799338b46f5f0420c3b082e7d84fade27a26
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830000"
---
# <a name="task-parallel-library-tpl"></a>タスク並列ライブラリ (TPL)

タスク並列ライブラリ (TPL: Task Parallel Library) は、<xref:System.Threading?displayProperty=nameWithType> 名前空間および <xref:System.Threading.Tasks?displayProperty=nameWithType> 名前空間におけるパブリック型と API のセットです。 TPL の目的は、アプリケーションに並列処理とコンカレンシーを追加するプロセスを簡略化して、開発者の生産性を高めることです。 TPL は、使用可能なすべてのプロセッサを最も効率的に使用するように、コンカレンシーの程度を動的に拡大します。 さらに TPL は、作業のパーティション分割、<xref:System.Threading.ThreadPool> 上のスレッドのスケジュール、キャンセルのサポート、状態管理、および他の低水準の詳細を処理します。 TPL を使用すると、コードのパフォーマンスが大幅に向上し、目的を達成するためのプログラミング作業に集中できます。  
  
 .NET Framework 4 以降でマルチスレッド コードおよび並列コードを作成する場合、TPL を使用することをお勧めします。 ただし、すべてのコードが並列処理に適しているわけではありません。 たとえば、ループの各反復処理で少量の作業しか実行されない場合、また反復処理が多数実行されない場合は、並列化のオーバーヘッドによってコードの実行が遅くなる場合があります。 さらに、マルチスレッド コードのような並列化によって、プログラムの実行がより複雑になります。 TPL はマルチスレッドのシナリオを簡略化しますが、たとえばロック、デッドロックおよび競合状態のスレッド処理の基本的な概念を理解し、TPL を効率的に使用することをお勧めします。  
  
## <a name="related-articles"></a>関連記事  
  
|Title|説明|  
|-|-|  
|[データの並列化](data-parallelism-task-parallel-library.md)|並列の `for` ループおよび `foreach` ループ (Visual Basic では `For` および `For Each`) を作成する方法について説明します。|  
|[タスク ベースの非同期プログラミング](task-based-asynchronous-programming.md)|<xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> を使用して暗黙的にタスクを作成および実行する方法、または <xref:System.Threading.Tasks.Task> オブジェクトを直接使用して明示的にタスクを作成および実行する方法について説明します。|  
|[データフロー](dataflow-task-parallel-library.md)|相互に非同期通信を行う必要がある複数の操作を処理する場合、またはデータが使用可能になったときにデータを処理する場合に、TPL データ フロー ライブラリのデータ フロー コンポーネントを使用する方法について説明します。|
|[データとタスクの並列化における注意点](potential-pitfalls-in-data-and-task-parallelism.md)|一般的な落とし穴とその回避方法について説明します。|  
|[Parallel LINQ (PLINQ)](introduction-to-plinq.md)|LINQ クエリでデータの並列化を達成する方法について説明します。|  
|[並列プログラミング](index.md)|.NET 並列プログラミングのトップ レベル ノード。|  
  
## <a name="see-also"></a>関連項目

- [.NET Core および .NET Standard による並列プログラミングのサンプル](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
