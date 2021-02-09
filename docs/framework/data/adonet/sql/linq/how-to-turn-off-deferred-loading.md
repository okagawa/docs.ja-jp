---
description: '詳細情報: 方法:遅延読み込みをオフにする'
title: '方法: 遅延読み込みをオフにする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 739c9b0b65eda73d6c504409395eb805b0c02873
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785836"
---
# <a name="how-to-turn-off-deferred-loading"></a>方法: 遅延読み込みをオフにする

<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> を `false` に設定すると、遅延読み込みをオフにできます。 詳細については、「[遅延読み込みと即時読み込み](deferred-versus-immediate-loading.md)」を参照してください。  
  
> [!NOTE]
> 遅延読み込みは、オブジェクト トラッキングをオフにすると暗黙でオフになります。 詳細については、[情報を読み取り専用として取得する](how-to-retrieve-information-as-read-only.md)」を参照してください。  
  
## <a name="example"></a>例  

 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> を `false` に設定して、遅延読み込みをオフにする方法を次の例に示します。  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [クエリの概念](query-concepts.md)
- [データベースに対するクエリの実行](querying-the-database.md)
