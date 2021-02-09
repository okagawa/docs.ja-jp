---
description: '詳細情報: DbDataAdapter を使用したデータの変更'
title: DbDataAdapter を使用したデータの変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: 749c56e8db76a469d7ebf0e503508665c2fdbd94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786252"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>DbDataAdapter を使用したデータの変更

<xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> オブジェクトの <xref:System.Data.Common.DbProviderFactory> メソッドを使用すると、ファクトリの作成時に指定した基になるデータ プロバイダーに対して厳密に型指定された <xref:System.Data.Common.DbDataAdapter> オブジェクトを取得できます。 続いて <xref:System.Data.Common.DbCommandBuilder> を使用することで、データ ソースに対して <xref:System.Data.DataSet> のデータの挿入、更新、削除を実行するコマンドを作成できます。  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>DbDataAdapter によるデータの取得  

 この例では、プロバイダー名と接続文字列に基づいて厳密に型指定された `DbDataAdapter` を作成する方法を示します。 このコード サンプルでは、<xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> の <xref:System.Data.Common.DbProviderFactory> メソッドを使用して、<xref:System.Data.Common.DbConnection> を作成します。 次に、<xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> メソッドを使用して <xref:System.Data.Common.DbCommand> を作成し、その `CommandText` プロパティと `Connection` プロパティを設定することでデータを選択します。 最後に、<xref:System.Data.Common.DbDataAdapter> メソッドを使用して <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> オブジェクトを作成し、その `SelectCommand` プロパティを設定します。 `Fill` の `DbDataAdapter` メソッドにより、データが <xref:System.Data.DataTable> に読み込まれます。  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>DbDataAdapter を使用したデータの変更  

 この例では、`DataTable` を使用してデータ ソースのデータの更新に必要なコマンドを生成することで、<xref:System.Data.Common.DbDataAdapter> を使用して <xref:System.Data.Common.DbCommandBuilder> のデータを変更する方法を示します。 <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> の `DbDataAdapter` は、Customers テーブルの CustomerID と CompanyName を取得するように設定されます。 <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> メソッドを使用して <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> プロパティを設定し、<xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> メソッドを使用して <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> プロパティを設定し、<xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> メソッドを使用して <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> プロパティを設定します。 Customers テーブルに新しい行が追加され、データ ソースが更新されます。 次に、CustomerID を検索して追加された行を特定します。この行が、Customers テーブルの主キーとなります。 これにより CompanyName が変更され、データ ソースが更新されます。 最後に、その行を削除します。  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>パラメーターの処理  

 .NET Framework のデータ プロバイダーによって、パラメーターおよびパラメーターのプレースホルダーの名前付けや指定方法が異なります。 次の表に示すように、データ ソースごとに固有の構文が採用されています。  
  
|データ プロバイダー|パラメーターの名前付け構文|  
|-------------------|-----------------------------|  
|`SqlClient`|`@`*parametername* 形式の名前付きパラメーターが使用されます。|  
|`OracleClient`|`:`*parmname* (または *parmname*) 形式の名前付きパラメーターが使用されます。|  
|`OleDb`|疑問符 (`?`) で指定される位置パラメーター マーカーが使用されます。|  
|`Odbc`|疑問符 (`?`) で指定される位置パラメーター マーカーが使用されます。|  
  
 ファクトリ モデルは、パラメーター化された `DbCommand` オブジェクトおよび `DbDataAdapter` オブジェクトの作成には利用できません。 コード内に分岐を作って、使用するデータ プロバイダーに対応したパラメーターを作成する必要があります。  
  
> [!IMPORTANT]
> プロバイダー固有のパラメーターを完全に回避するために、文字列の連結を利用して直接 SQL ステートメントを作成することは、セキュリティ上の理由から推奨されません。 パラメーターではなく文字列の連結を利用した場合、アプリケーションが SQL インジェクション攻撃に対して脆弱になります。  
  
## <a name="see-also"></a>関連項目

- [DbProviderFactories](dbproviderfactories.md)
- [DbProviderFactory の取得](obtaining-a-dbproviderfactory.md)
- [DbConnection、DbCommand、および DbException](dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET の概要](ado-net-overview.md)
