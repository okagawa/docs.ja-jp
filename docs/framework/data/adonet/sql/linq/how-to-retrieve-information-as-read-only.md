---
description: '詳細情報: 方法:情報を読み取り専用として取得する'
title: '方法: 情報を読み取り専用として取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 7743e555bcc3f6371ca601d02313e30895e57961
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723453"
---
# <a name="how-to-retrieve-information-as-read-only"></a>方法: 情報を読み取り専用として取得する

データを変更する予定がない場合は、読み取り専用の結果を取得することでクエリのパフォーマンスを向上させることができます。  
  
 読み取り専用の処理を実装するには、<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> を `false` に設定します。  
  
> [!NOTE]
> <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> を `false` に設定すると、<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> が暗黙的に `false` に設定されます。  
  
## <a name="example"></a>例  

 次のコード例は、従業員の入社日の読み取り専用コレクションを取得します。  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [クエリの概念](query-concepts.md)
- [データベースに対するクエリの実行](querying-the-database.md)
- [遅延読み込みと即時読み込み](deferred-versus-immediate-loading.md)
