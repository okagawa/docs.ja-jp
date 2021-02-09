---
description: '詳細情報: 型指定されたデータセットのクエリを実行する'
title: 型指定された DataSet のクエリ
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 5bcf8bb587a0ed0eaca1bbe9b3a7d7143757780e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723700"
---
# <a name="query-typed-datasets"></a>型指定されたデータセットのクエリを実行する

アプリケーションの設計時に <xref:System.Data.DataSet> のスキーマがわかっている場合は、LINQ to DataSet を使用するときに、型指定された <xref:System.Data.DataSet> を用いることをお勧めします。 型指定された <xref:System.Data.DataSet> とは、<xref:System.Data.DataSet> から派生されたクラスのことです。 したがって、型指定されたデータセットは <xref:System.Data.DataSet> のすべてのメソッド、イベント、およびプロパティを継承します。 さらに、型指定された <xref:System.Data.DataSet> には、厳密に型指定されたメソッド、イベント、プロパティが用意されています。 つまり、コレクションベースのメソッドを使用せずに名前でテーブルおよび列にアクセスできます。 これによりクエリが簡素化され、読みやすくなります。 詳しくは、「[型指定されたデータセット](./dataset-datatable-dataview/typed-datasets.md)」をご覧ください。

LINQ to DataSet では、型指定された <xref:System.Data.DataSet> に対するクエリもサポートされています。 型指定された <xref:System.Data.DataSet> では、列データにアクセスするために、ジェネリック メソッドの <xref:System.Data.DataRowExtensions.Field%2A> または <xref:System.Data.DataRowExtensions.SetField%2A> を使用する必要はありません。 <xref:System.Data.DataSet> に型情報が含まれているため、プロパティ名をコンパイル時に利用できます。 LINQ to DataSet では、適切な型として列の値にアクセスできるため、実行時ではなくコードのコンパイル時に型の不一致エラーがキャッチされます。

型指定された <xref:System.Data.DataSet> に対してクエリを実行するには、Visual Studio の **データセット デザイナー** を使用してあらかじめクラスを生成しておく必要があります。 詳しくは、「[データセットを作成および構成する](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)」をご覧ください。

## <a name="example"></a>例

次の例では、型指定された <xref:System.Data.DataSet> に対してクエリを実行しています。

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a>関連項目

- [DataSet のクエリ](querying-datasets-linq-to-dataset.md)
- [複数テーブルにまたがるクエリ](cross-table-queries-linq-to-dataset.md)
- [単一テーブルのクエリ](single-table-queries-linq-to-dataset.md)
