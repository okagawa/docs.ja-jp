---
description: '詳細情報: ADO.NET でのデータ ソースへの接続'
title: データ ソースへの接続
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 0bf66b9dc609a704cf89380e2376f50197e047a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663886"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>ADO.NET でのデータ ソースへの接続

ADO.NET では、**Connection** オブジェクトを使用して、接続文字列に必要な認証情報を指定することにより、特定のデータ ソースに接続します。 どの **Connection** オブジェクトを使用するかは、データ ソースの種類によって異なります。  
  
 .NET Framework に含まれている各 .NET Framework データ プロバイダーは、<xref:System.Data.Common.DbConnection> オブジェクトを持っています。.NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbConnection> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlConnection> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcConnection> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleConnection> があります。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [接続の確立](establishing-the-connection.md)\
 **Connection** オブジェクトを使用して、データ ソースとの接続を確立する方法について説明します。  
  
 [接続イベント](connection-events.md)\
 **InfoMessage** イベントを使用してデータ ソースから情報メッセージを取得する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [接続文字列](connection-strings.md)
- [接続プール](connection-pooling.md)
- [コマンドおよびパラメーター](commands-and-parameters.md)
- [DataAdapter と DataReader](dataadapters-and-datareaders.md)
- [トランザクションとコンカレンシー](transactions-and-concurrency.md)
- [ADO.NET の概要](ado-net-overview.md)
