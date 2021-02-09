---
description: '詳細情報: 方法:ADO.NET コマンドおよび DataContext 間の接続を再利用する'
title: '方法: ADO.NET コマンドおよび DataContext 間の接続を再利用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: d5bf45dfd705ed6e9b9d4ed9659e01bfcb539df2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785953"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>方法: ADO.NET コマンドおよび DataContext 間の接続を再利用する

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は ADO.NET テクノロジ ファミリの一部であり、ADO.NET によって提供されるサービスに基づいているため、ADO.NET のコマンドと <xref:System.Data.Linq.DataContext> の間の接続を再利用できます。  
  
## <a name="example"></a>例  

 次の例では、ADO.NET のコマンドと <xref:System.Data.Linq.DataContext> の間の同じ接続を再利用する方法を示します。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [背景情報](background-information.md)
- [ADO.NET および LINQ to SQL](ado-net-and-linq-to-sql.md)
- [データベースとの通信](communicating-with-the-database.md)
