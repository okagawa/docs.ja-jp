---
description: '詳細情報: OLE DB データ型のマッピング'
title: OLE DB データ型のマッピング
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: 8dd750754a67921437ca9b8fac751857961385cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786187"
---
# <a name="ole-db-data-type-mappings"></a>OLE DB データ型のマッピング

次の表では、.NET Framework Data Provider for ADO および OLE DB (<xref:System.Data.OleDb>) のデータ型から推論される .NET Framework の型を示します。 <xref:System.Data.OleDb.OleDbDataReader> の型指定されたアクセサー メソッドも示します。  
  
|ADO 型|OLE DB 型|.NET Framework 型|.NET Framework の型指定されたアクセサー|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|ブール型|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|String|GetString()|  
|adChapter|DBTYPE_HCHAPTER|`DataReader` によってサポートされます。 「[DataReader によるデータの取得](retrieving-data-using-a-datareader.md)」をご覧ください。|GetValue()|  
|adChar|DBTYPE_STR|String|GetString()|  
|adCurrency|DBTYPE_CY|Decimal (10 進数型)|GetDecimal()|  
|adDate|DBTYPE_DATE|DateTime|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DateTime|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DateTime|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DateTime|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Decimal (10 進数型)|GetDecimal()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException|GetValue()|  
|adFileTime|DBTYPE_FILETIME|DateTime|GetDateTime()|  
|adGUID|DBTYPE_GUID|GUID|GetGuid()|  
|adIDispatch|DBTYPE_IDISPATCH *|Object|GetValue()|  
|adInteger|DBTYPE_I4|Int32|GetInt32()|  
|adIUnknown|DBTYPE_IUNKNOWN *|Object|GetValue()|  
|adNumeric|DBTYPE_NUMERIC|Decimal (10 進数型)|GetDecimal()|  
|adPropVariant|DBTYPE_PROPVARIANT|Object|GetValue()|  
|adSingle|DBTYPE_R4|Single|GetFloat()|  
|adSmallInt|DBTYPE_I2|Int16|GetInt16()|  
|adTinyInt|DBTYPE_I1|Byte|GetByte()|  
|adUnsignedBigInt|DBTYPE_UI8|UInt64|GetValue()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue()|  
|adUnsignedTinyInt|DBTYPE_UI1|Byte|GetByte()|  
|adVariant|DBTYPE_VARIANT|Object|GetValue()|  
|adWChar|DBTYPE_WSTR|String|GetString()|  
|adUserDefined|DBTYPE_UDT|サポート外||  
|adVarNumeric|DBTYPE_VARNUMERIC|サポート外||  
  
 \* OLE DB の `DBTYPE_IUNKNOWN` 型と `DBTYPE_IDISPATCH` 型の場合、オブジェクト参照はポインターのマーシャリングされた表現です。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET でのデータの取得および変更](retrieving-and-modifying-data.md)
- [ADO.NET の概要](ado-net-overview.md)
