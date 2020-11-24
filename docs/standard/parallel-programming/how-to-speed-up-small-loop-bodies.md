---
title: '方法: 小さいループ本体を高速化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
ms.openlocfilehash: 0e6e32386992a5dc4ac4556bc9d0489d0fd9d289
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826828"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>方法: 小さいループ本体を高速化する
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ループの本体が小さい場合、[for](../../csharp/language-reference/keywords/for.md) ループ (C#)、[For](/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) ループ (Visual Basic) など、同等の連続したループよりパフォーマンスが低下する可能性があります。 パフォーマンスの低下は、データのパーティション分割と、各ループのイテレーションでデリゲートを呼び出す負荷によって発生します。 このようなシナリオに対処するため、<xref:System.Collections.Concurrent.Partitioner> クラスには <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> メソッドが用意されています。このメソッドにより、デリゲートがイテレーションごとに 1 回ではなく、パーティションごとに 1 回だけ呼び出されるように、デリゲートの本体に順次ループを提供できるようになります。 詳細については、「[Custom Partitioners for PLINQ and TPL (PLINQ および TPL 用のカスタム パーティショナー)](custom-partitioners-for-plinq-and-tpl.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 この例で示す方法は、ループが最小限の作業を実行するときに便利です。 作業がより負荷の大きい処理になるにつれ、既定のパーティショナーで <xref:System.Threading.Tasks.Parallel.For%2A> ループまたは <xref:System.Threading.Tasks.Parallel.ForEach%2A> ループを使用すると、同じまたはそれ以上のパフォーマンスが得られることがあります。  
  
## <a name="see-also"></a>参照

- [データの並列化](data-parallelism-task-parallel-library.md)
- [PLINQ および TPL 用のカスタム パーティショナー](custom-partitioners-for-plinq-and-tpl.md)
- [反復子 (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [反復子 (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [PLINQ および TPL のラムダ式](lambda-expressions-in-plinq-and-tpl.md)
