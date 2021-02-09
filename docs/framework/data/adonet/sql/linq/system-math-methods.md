---
description: '詳細情報: System.Math メソッド'
title: System.Math メソッド
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: e97e0a16b6eafdb57f4aaf72d62788e6657afbdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681345"
---
# <a name="systemmath-methods"></a>System.Math メソッド

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の <xref:System.Math> メソッドをサポートしていません。  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>.NET との相違  

 .NET Framework で使用される丸めセマンティクスは SQL Server とは異なります。 .NET Framework の <xref:System.Math.Round%2A> メソッドでは、"*銀行型丸め*" が実行されます。銀行型丸めでは、.5 で終わる数値は次の桁に切り上げられるのではなく、最も近い偶数になるように丸められます。 たとえば、2.5 は 2 に丸められ、3.5 は 4 に丸められます  (この方法は、大規模なデータ トランザクションで、値が大きくなる組織的バイアスの回避に役立ちます)。  
  
 SQL では、`ROUND` 関数は常に、0 から遠ざかる方向に丸めを実行します。 したがって、2.5 は 3 に丸められます。これは、2 に丸められる .NET Framework とは対照的です。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、SQL の `ROUND` セマンティクスに到達するため、銀行型丸めを実装しようとしません。  
  
## <a name="see-also"></a>関連項目

- [データ型と関数](data-types-and-functions.md)
