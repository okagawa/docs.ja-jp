---
title: 大きい値 (max) データの変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 00a4ae83270bb74e9703faebfc93e26b5c069478
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174278"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>ADO.NET での大きい値 (max) データの変更
ラージ オブジェクト (LOB) データ型は、最大行サイズが 8 KB を超えるデータ型です。 SQL Server では、`max`、`varchar`、および `nvarchar` の各データ型に `varbinary` 指定子が用意されており、2^32 バイトの値を格納できます。 テーブル列および Transact-SQL 変数により、`varchar(max)`、`nvarchar(max)`、または `varbinary(max)` データ型を指定できます。 ADO.NET では、`max` データ型は、`DataReader` によってフェッチすることができ、特殊な処理を行うことなく入力パラメーターと出力パラメーター両方の値として指定することもできます。 サイズの大きい `varchar` データ型の場合は、データを段階的に取得および更新できます。  
  
 `max` データ型は、Transact-SQL 変数として比較に使用したり、連結に使用したりできます。 これらは SELECT ステートメントの DISTINCT 句、ORDER BY 句、GROUP BY 句で使用できるほか、集約、結合、サブクエリでも使用できます。  
  
 次の表は、SQL Server オンライン ブックのドキュメントへのリンクを提供します。  
  
 **SQL Server のドキュメント**  
  
1. [大きな値のデータ型の使用](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))  
  
## <a name="large-value-type-restrictions"></a>大きい値型の制限事項  
 `max` データ型には、小さいデータ型にはない、次の制限事項が適用されます。  
  
- `sql_variant` に大きな `varchar` データ型を含めることはできません。  
  
- 大きな `varchar` 列を、インデックスのキー列として指定することはできません。 この列は、非クラスター化インデックスの付加列で許可されます。  
  
- 大きい `varchar` 列はパーティション分割のキー列として使用できません。  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Transact-SQL での大きい値型の使用  
 Transact-SQL の `OPENROWSET` 関数は、リモート データへの接続およびアクセスに 1 回だけ使用できます。 この関数には、OLE DB データ ソースからリモート データにアクセスするために必要な、すべての接続情報が含まれています。 `OPENROWSET` は、クエリの FROM 句でテーブル名と同様に参照できます。 OLE DB プロバイダーの機能に従って、INSERT、UPDATE、または DELETE ステートメントのターゲット テーブルとして参照することもできます。  
  
 `OPENROWSET` 関数には、`BULK` 行セット プロバイダーが含まれており、データをターゲット テーブルに読み込むことなく、ファイルから直接読み取ることができます。 これにより、`OPENROWSET` を単純な INSERT SELECT ステートメントで使用できます。  
  
 `OPENROWSET BULK` オプション引数により、データの読み取りの開始位置および終了位置、エラーの処理、データの解釈の制御が大幅に容易になります。 たとえば、データ ファイルを 1 行として、あるいは `varbinary`、`varchar`、または `nvarchar` 型の 1 列の行セットとして読み取るように指定できます。 完全な構文とオプションについては、SQL Server オンライン ブックを参照してください。  
  
 次の例は、写真を、AdventureWorks サンプル データベースの ProductPhoto テーブルに挿入しています。 `BULK OPENROWSET` プロバイダーを使用する場合は、すべての列に値を挿入しない場合でも、列名を挙げてリストを作成する必要があります。 この場合の主キーは ID 列として定義され、列リストから省略できます。 また、`OPENROWSET` ステートメントの末尾で相関関係名を指定する必要があることにも注意してください。この例では ThumbnailPhoto です。 これにより、ファイルが読み込まれる `ProductPhoto` テーブルの列との相関関係が定義されます。  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,
    ThumbnailPhotoFilePath,
    LargePhoto,
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>UPDATE .WRITE を使用したデータの更新  
 Transact-SQL の UPDATE ステートメントでは、`varchar(max)`、`nvarchar(max)`、または `varbinary(max)` 列の内容を変更するための、新しい WRITE 構文を使用できます。 これにより、データを部分的に更新できます。 ここでは省略形式で UPDATE .WRITE 構文が示されています。  
  
 UPDATE  
  
 { *\<object>* }  
  
 SET  
  
 { *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }  
  
 WRITE メソッドは、*column_name* の値のセクションが変更されることを指定します。 この式は *column_name* にコピーされる値で、`@Offset` は式が記述される開始位置であり、`@Length` 引数は列のセクションの長さを示します。  
  
|If|Then|  
|--------|----------|  
|式が NULL に設定されています|`@Length` は無視され、*column_name* の値は指定された `@Offset` で切り捨てられます。|  
|`@Offset` が NULL|更新操作によって既存の *column_name* の値の最後に式が追加され、`@Length` が無視されます。|  
|`@Offset` が column_name 値の長さを超えています|SQL Server はエラーを返します。|  
|`@Length` が NULL|更新操作により `@Offset` の値の `column_name` から最後までのすべてのデータが削除されます。|  
  
> [!NOTE]
> `@Offset` も `@Length` も負の数にすることはできません。  
  
## <a name="example"></a>例  
 この Transact-SQL の例では、AdventureWorks データベースの Document テーブルの `nvarchar(max)` 列である DocumentSummary の部分値を更新します。 置換後の単語、置換する単語の既存データ内での開始位置 (オフセット)、置換する文字数 (長さ) を指定することで、'components' という単語が 'features' という単語に置換されます。 この例では、結果を比較するために、UPDATE ステートメントの前後に SELECT ステートメントを指定しています。  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>ADO.NET での大きい値型の使用  
 大きい値型を ADO.NET で使用するには、大きい値型を <xref:System.Data.SqlClient.SqlDataReader> で <xref:System.Data.SqlClient.SqlParameter> オブジェクトとして指定して結果セットを返すようにするか、<xref:System.Data.SqlClient.SqlDataAdapter> を使用して `DataSet`/`DataTable` に入力します。 大きな値の型と、それに関連する小さい値のデータ型の操作方法に違いはありません。  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>GetSqlBytes を使用したデータ取得  
 <xref:System.Data.SqlClient.SqlDataReader> の `GetSqlBytes` メソッドを使用して、`varbinary(max)` 列の内容を取得できます。 次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlCommand> という名前の `cmd` オブジェクトによってテーブルから `varbinary(max)` データが選択され、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが <xref:System.Data.SqlTypes.SqlBytes> として取得されることを想定しています。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>GetSqlChars を使用したデータの取得  
 `GetSqlChars` の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、`varchar(max)` または `nvarchar(max)` 列の内容を取得できます。 次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlCommand> という名前の `cmd` オブジェクトによってテーブルから `nvarchar(max)` データが選択され、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが取得されることを想定しています。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>GetSqlBinary を使用したデータの取得  
 `GetSqlBinary` の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、`varbinary(max)` 列の内容を取得できます。 次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlCommand> という名前の `cmd` オブジェクトによってテーブルから `varbinary(max)` データが選択され、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが <xref:System.Data.SqlTypes.SqlBinary> ストリームとして取得されることを想定しています。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>GetBytes を使用したデータの取得  
 `GetBytes` の <xref:System.Data.SqlClient.SqlDataReader> メソッドにより、指定された配列のオフセットから開始するバイト配列に、指定された列のオフセットからバイトのストリームが読み込まれます。 次のコード フラグメントは、バイト配列に対するバイトを取得する `reader` という名前の <xref:System.Data.SqlClient.SqlDataReader> オブジェクトがあることを前提としています。 ただし `GetSqlBytes` とは異なり、`GetBytes` では配列バッファーのサイズを指定する必要があります。  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>GetValue を使用したデータの取得  
 `GetValue` の <xref:System.Data.SqlClient.SqlDataReader> メソッドにより、指定した列オフセットから値が配列に読み込まれます。 次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによって、最初の列のオフセットからバイナリ データが取得され、2 番目の列のオフセットから文字列データが取得されることが想定されています。  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>大きい値型から CLR 型への変換  
 `varchar(max)` などの任意の文字列変換メソッドを使用して、`nvarchar(max)` または `ToString` 列の内容を変換できます。 次のコード フラグメントは、データを取得する `reader` という名前の <xref:System.Data.SqlClient.SqlDataReader> オブジェクトがあることを前提としています。  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>例  
 次のコードでは、`AdventureWorks` データベースの `ProductPhoto` テーブルから名前と `LargePhoto` オブジェクトを取得し、ファイルに保存します。 アセンブリは、<xref:System.Drawing> 名前空間への参照を使用してコンパイルする必要があります。  <xref:System.Data.SqlClient.SqlDataReader> の <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> メソッドは、`Stream` プロパティを公開する <xref:System.Data.SqlTypes.SqlBytes> オブジェクトを返します。 コードではこのオブジェクトを使用して新しい `Bitmap` オブジェクトが作成され、Gif `ImageFormat` に保存されます。  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>大きな値型パラメーターの使用  
 大きい値型は、<xref:System.Data.SqlClient.SqlParameter> オブジェクト内の小さい値型と同じ方法で、<xref:System.Data.SqlClient.SqlParameter> オブジェクト内で使用できます。 次の例に示すように、大きい値型は <xref:System.Data.SqlClient.SqlParameter> 値として取得することができます。 このコードは、次の GetDocumentSummary ストアド プロシージャが AdventureWorks サンプル データベースに存在することを前提としています。 ストアド プロシージャでは @DocumentID という名前の入力パラメーターを受け取り、@DocumentSummary 出力パラメーターの DocumentSummary 列の内容を返します。  
  
```sql
CREATE PROCEDURE GetDocumentSummary
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a>例  
 ADO.NET コードは <xref:System.Data.SqlClient.SqlConnection> オブジェクトと <xref:System.Data.SqlClient.SqlCommand> オブジェクトを作成して GetDocumentSummary ストアド プロシージャを実行し、大きな値型として格納されているドキュメントの概要を取得します。 このコードによって @DocumentID 入力パラメーターの値が渡され、@DocumentSummary 出力パラメーターに戻された結果がコンソール ウィンドウに表示されます。  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [SQL Server のバイナリ データと大きな値のデータ](sql-server-binary-and-large-value-data.md)
- [SQL Server データ型のマッピング](../sql-server-data-type-mappings.md)
- [ADO.NET における SQL Server データ操作](sql-server-data-operations.md)
- [ADO.NET の概要](../ado-net-overview.md)
