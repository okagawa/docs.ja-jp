---
description: '詳細情報: SqlTypes と DataSet'
title: SqlTypes と DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: 088c1cdc65b3c79a77e0bf724b5550c001a40554
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766999"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes と DataSet

ADO.NET 2.0 では、`DataSet` 名前空間を介した <xref:System.Data.SqlTypes> の型のサポートが拡張されました。 <xref:System.Data.SqlTypes> の型は、SQL Server データベースのデータ型と同じセマンティクスおよび精度を持つデータ型を提供することを目的にデザインされています。 <xref:System.Data.SqlTypes> の個々のデータ型には、それに相当する SQL Server のデータ型があり、基本となるデータ表現はいずれも同じです。  
  
 <xref:System.Data.DataSet> で <xref:System.Data.SqlTypes> を直接使用すると、SQL Server データ型を操作する際にいくつかの利点があります。 <xref:System.Data.SqlTypes> では、SQL Server ネイティブのデータ型と同じセマンティクスがサポートされています。 <xref:System.Data.SqlTypes> の定義でいずれかの <xref:System.Data.DataColumn> を指定することで、decimal データ型または numeric データ型をいずれかの共通言語ランタイム (CLR) データ型に変換するときの精度の低下を防止します。  
  
## <a name="example"></a>例  

 次の例では、<xref:System.Data.DataTable> オブジェクトを作成し、CLR データ型の代わりに <xref:System.Data.DataColumn> を使用して、<xref:System.Data.SqlTypes> のデータ型を明示的に定義します。 このコードは、SQL Server の AdventureWorks データベースの Sales.SalesOrderDetail テーブルから取得されたデータを <xref:System.Data.DataTable> に挿入します。 コンソール ウィンドウには、各列のデータ型および SQL Server から取得された値が表示されます。  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [SQL Server データ型のマッピング](../sql-server-data-type-mappings.md)
- [パラメーターおよびパラメーター データ型の構成](../configuring-parameters-and-parameter-data-types.md)
- [ADO.NET の概要](../ado-net-overview.md)
