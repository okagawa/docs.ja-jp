---
description: '詳細については、次を参照してください: IMetaDataTables 許容:: GetTableInfo メソッド'
title: IMetaDataTables::GetTableInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
ms.openlocfilehash: 3929f91c15b5c1fc22ac3ad4b17cbaa38a08533a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687650"
---
# <a name="imetadatatablesgettableinfo-method"></a>IMetaDataTables::GetTableInfo メソッド

指定されたテーブルの名前、行のサイズ、行数、列の数、およびキー列のインデックスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ixTbl`  
 から返されるプロパティを持つテーブルの識別子。  
  
 `pcbRow`  
 入出力テーブル行のサイズ (バイト単位) へのポインター。  
  
 `pcRows`  
 入出力テーブル内の行の数へのポインター。  
  
 `pcCols`  
 入出力テーブル内の列数へのポインター。  
  
 `piKey`  
 入出力キー列のインデックスへのポインター。テーブルにキー列がない場合は-1。  
  
 `ppName`  
 入出力テーブル名へのポインターへのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataTables インターフェイス](imetadatatables-interface.md)
- [IMetaDataTables2 インターフェイス](imetadatatables2-interface.md)
