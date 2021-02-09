---
description: '詳細情報: AutoIncrement 列の作成'
title: AutoIncrement 列の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 7568b1013b7af5aef7a6fc1f28dc163a082743a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739639"
---
# <a name="creating-autoincrement-columns"></a>AutoIncrement 列の作成

列値を一意にするために、新しい行がテーブルに追加されたときに列値が自動的にインクリメントされるように設定できます。 自動インクリメント <xref:System.Data.DataColumn> を作成するには、列の <xref:System.Data.DataColumn.AutoIncrement%2A> プロパティを **true** に設定します。 <xref:System.Data.DataColumn> の値は <xref:System.Data.DataColumn.AutoIncrementSeed%2A> プロパティで定義された値から開始され、行が追加されるたびに、**AutoIncrement** 列の値には、列の <xref:System.Data.DataColumn.AutoIncrementStep%2A> プロパティで定義された値が加算されます。  
  
 **AutoIncrement** 列では、**DataColumn** の <xref:System.Data.DataColumn.ReadOnly%2A> プロパティを **true** に設定することをお勧めします。  
  
 値 200 から開始して 3 ずつインクリメントする列を作成する方法を次の例に示します。  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataColumn>
- [DataTable スキーマの定義](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET の概要](../ado-net-overview.md)
