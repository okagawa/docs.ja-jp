---
title: IMetaDataTables2::GetMetaDataStreamInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
ms.openlocfilehash: 21fc79f62dba4b16a7a067dff8fb9dcc795c9d35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708726"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a>IMetaDataTables2::GetMetaDataStreamInfo メソッド

指定したインデックス位置にあるメタデータストリームの名前、サイズ、および内容を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ix`  
 から要求されたメタデータストリームのインデックス。  
  
 `ppchName`  
 入出力ストリームの名前へのポインター。  
  
 `ppv`  
 入出力メタデータストリームへのポインター。  
  
 `pcb`  
 入出力のサイズ (バイト単位) `ppv` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataTables2 インターフェイス](imetadatatables2-interface.md)
- [IMetaDataTables インターフェイス](imetadatatables-interface.md)
