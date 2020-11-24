---
title: '方法: 並列タスクでバイナリ ツリーを走査する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
ms.openlocfilehash: ca70021c7d071abe480cb4ed866e34f171cc3b45
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825534"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>方法: 並列タスクでバイナリ ツリーを走査する
次の例では、ツリー データ構造を走査する並列タスクを使用する 2 つの方法を示します。 ツリー自体の作成は、演習として残しておきます。  
  
## <a name="example"></a>例  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 示した 2 つのメソッドは、機能的に同等です。 タスクを作成して実行するために、<xref:System.Threading.Tasks.TaskFactory.StartNew%2A> メソッドを使用すると、タスクで待機し、例外を処理するために使用するタスクからハンドルを戻すことができます。  
  
## <a name="see-also"></a>参照

- [タスク並列ライブラリ (TPL)](task-parallel-library-tpl.md)
