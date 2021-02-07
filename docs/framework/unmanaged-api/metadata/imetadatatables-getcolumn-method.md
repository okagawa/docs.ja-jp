---
description: '詳細については、次を参照してください: IMetaDataTables 許容:: GetColumn メソッド'
title: IMetaDataTables::GetColumn メソッド
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: 4c4cec7216f93783b34b594330358d1e6036ed40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688274"
---
# <a name="imetadatatablesgetcolumn-method"></a>IMetaDataTables::GetColumn メソッド

指定したテーブル内の指定した列および行のセルに格納されている値へのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a>パラメーター

 `ixTbl`  
 からテーブルのインデックス。  
  
 `ixCol`  
 からテーブル内の列のインデックス。  
  
 `rid`  
 からテーブル内の行のインデックス。  
  
 `pVal`  
 入出力セル内の値へのポインター。  

## <a name="remarks"></a>解説

によって返される値の interpretion は、 `pVal` 列の型によって異なります。 列の型は、 [GetColumnInfo](imetadatatables-getcolumninfo-method.md)を呼び出すことによって決定できます。

- **Getcolumn** メソッドは、 **Rid** または **codedtoken** 型の列を、完全な32ビット値に自動的に変換し `mdToken` ます。
- また、8ビットまたは16ビットの値を完全な32ビット値に自動的に変換します。
- *ヒープ* 型の列の場合、返される *pVal* は、対応するヒープのインデックスになります。

| 列の型              | pVal を含む | 解説                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)  | mdToken     | *pVal* には完全なトークンが含まれます。 関数は、自動的に Rid を完全なトークンに変換します。 |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | mdToken | 返されると、 *pVal* には完全なトークンが含まれます。 関数は、CodedToken を完全なトークンに自動的に圧縮解除します。 |
| `iSHORT` (96)            | Int16         | 32ビットに自動的に拡張されます。  |
| `iUSHORT` (97)           | UInt16        | 32ビットに自動的に拡張されます。  |
| `iLONG` (98)             | Int32         |                                        |
| `iULONG` (99)            | UInt32        |                                        |
| `iBYTE` (100)            | Byte          | 32ビットに自動的に拡張されます。  |
| `iSTRING` (101)          | 文字列ヒープインデックス | *pVal* は、文字列ヒープのインデックスです。 実際の列文字列値を取得するには、 [Imetadatatables::](imetadatatables-getstring-method.md) を使用します。 |
| `iGUID` (102)            | Guid ヒープインデックス | *pVal* は、Guid ヒープのインデックスです。 実際の列の Guid 値を取得するには、 [Imetadatatables 指定できる:: GetGuid](imetadatatables-getguid-method.md) を使用します。 |
| `iBLOB` (103)            | Blob ヒープインデックス | *pVal* は、Blob ヒープのインデックスです。 実際の列の Blob 値を取得するには、 [Imetadatatables 指定できる:: GetBlob](imetadatatables-getblob-method.md) を使用します。 |
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataTables インターフェイス](imetadatatables-interface.md)
- [IMetaDataTables2 インターフェイス](imetadatatables2-interface.md)
