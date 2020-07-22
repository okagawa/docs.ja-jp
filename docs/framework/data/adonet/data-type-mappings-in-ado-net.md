---
title: データ型のマップ
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 610cdc1a679b0c51125075076120e12db97da421
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980198"
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET でのデータ型のマッピング
.NET Framework は共通型システムを基にしています。このシステムは実行時の型の宣言、使用、および管理方法を定義するものです。 値型と参照型の両方から構成されており、これらはすべて <xref:System.Object> 基本型から派生します。 データ ソースを操作するときは、データ型が明示的に指定されていない場合はデータ プロバイダーから推論されます。 たとえば、<xref:System.Data.DataSet> オブジェクトは、特定のデータ ソースには依存しません。 `DataSet` 内のデータはデータ ソースから取得され、変更は `DataAdapter` によってデータ ソースに反映されます。 つまり、`DataAdapter` によって `DataSet` 内の <xref:System.Data.DataTable> に、データ ソースからの値が格納されると、`DataTable` 内の列の結果のデータ型は、データ ソースへの接続に使用された .NET Framework データ プロバイダーに固有の型ではなく、.NET Framework の型になります。  
  
 同様に、`DataReader` によってデータ ソースから値が返されるとき、結果の値は .NET Framework 型のローカル変数に格納されます。 `DataAdapter` の `Fill` 操作と `DataReader` の `Get` メソッドのどちらの場合も、.NET Framework の型は .NET Framework データ プロバイダーから返された値から推論されます。  
  
 返される値の型がわかっている場合は、推論されるデータ型を使用するのではなく、`DataReader` の型指定されたアクセサー メソッドを使用できます。 型指定されたアクセサー メソッドを使用して .NET Framework の特定の型として値を返すと、追加の型変換が不要になるため、パフォーマンスが向上します。  
  
> [!NOTE]
> .NET Framework データ プロバイダーのデータ型の null 値は、`DBNull.Value` で表されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL Server データ型のマッピング](sql-server-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.SqlClient> のデータ アクセサー メソッドを一覧で示します。  
  
 [OLE DB データ型のマッピング](ole-db-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.OleDb> のデータ アクセサー メソッドを一覧で示します。  
  
 [ODBC データ型のマッピング](odbc-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.Odbc> のデータ アクセサー メソッドを一覧で示します。  
  
 [Oracle データ型のマッピング](oracle-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.OracleClient> のデータ アクセサー メソッドを一覧で示します。  
  
 [浮動小数点数](floating-point-numbers.md)  
 開発者が浮動小数点数を扱う際の発生頻度の高い問題について説明します。  
  
## <a name="see-also"></a>関連項目

- [SQL Server データ型と ADO.NET](./sql/sql-server-data-types.md)
- [パラメーターおよびパラメーター データ型の構成](configuring-parameters-and-parameter-data-types.md)
- [データベース スキーマ情報の取得](retrieving-database-schema-information.md)
- [共通型システム](../../../standard/base-types/common-type-system.md)
- [型の変換](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET の概要](ado-net-overview.md)
