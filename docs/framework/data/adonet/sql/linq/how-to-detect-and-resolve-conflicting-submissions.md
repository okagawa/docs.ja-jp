---
description: '詳細情報: 方法:送信の競合を検出および解決する'
title: '方法: 送信の競合を検出および解決する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 7ccfc9aeba8a21c3f5e950569d7650af087416a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739041"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>方法: 送信の競合を検出および解決する

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] には、複数のユーザーがデータベースを変更するために生じる競合を、検出および解決するための多くのリソースが用意されています。 詳細については、[変更の競合を管理する](how-to-manage-change-conflicts.md)」を参照してください。  
  
## <a name="example"></a>例  

 <xref:System.Data.Linq.ChangeConflictException> 例外をキャッチする `try`/`catch` ブロックの例を次にします。 各競合のエンティティおよびメンバー情報が、コンソール ウィンドウに表示されます。  
  
> [!NOTE]
> 情報の取得をサポートするには、`using System.Reflection` ディレクティブ (Visual Basic の場合は `Imports System.Reflection`) を含める必要があります。 詳細については、「<xref:System.Reflection>」を参照してください。  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [データの変更と変更の送信](making-and-submitting-data-changes.md)
- [方法: 変更の競合を管理する](how-to-manage-change-conflicts.md)
