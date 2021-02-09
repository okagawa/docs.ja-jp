---
description: '詳細情報: AcceptChange と RejectChange'
title: AcceptChange と RejectChange
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: e21952063bf27f4f969669eb76b964fc7537b59a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725260"
---
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChange と RejectChange

<xref:System.Data.DataTable> 内のデータに行われた変更が正確であるかどうかを検証した後で、<xref:System.Data.DataRow>、<xref:System.Data.DataTable>、または <xref:System.Data.DataSet> の <xref:System.Data.DataRow.AcceptChanges%2A> メソッドを使用して、変更を受け入れることができます。変更を受け入れると、**Current** 行の値が **Original** の値に設定され、**RowState** プロパティが **Unchanged** に設定されます。 変更を受け入れるかまたは拒否すると、**RowError** 情報が削除され、**HasErrors** プロパティが **false** に設定されます。 変更を受け入れるかまたは拒否した場合、データ ソース内で実行中の更新操作にも影響することがあります。 詳しくは、「[DataAdapter によるデータ ソースの更新](../updating-data-sources-with-dataadapters.md)」をご覧ください。  
  
 **DataTable** に外部キー制約が存在する場合、**AcceptChanges** と **RejectChanges** を使用して受け入れられた変更または拒否された変更は、**ForeignKeyConstraint.AcceptRejectRule** に従って **DataRow** の子の行に反映されます。 詳しくは、「[DataTable の制約](datatable-constraints.md)」をご覧ください。  
  
 行にエラーがあるかどうかをチェックし、必要に応じてエラーを解決し、エラーを解決できない場合にはその行を拒否する例を次に示します。 解決されたエラーについては、**RowError** 値が空の文字列にリセットされるため、**HasErrors** プロパティが **false** に設定されます。 エラーのある行がすべて解決または拒否された時点で、**DataTable** 全体に対するすべての変更を受け入れるために、**AcceptChanges** が呼び出されます。  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataTable 内のデータの操作](manipulating-data-in-a-datatable.md)
- [ADO.NET の概要](../ado-net-overview.md)
