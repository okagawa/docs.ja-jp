---
title: IMetaDataImport::GetClassLayout メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 5a442d8d0916b0e86f25c03507de66fc999f2159
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711261"
---
# <a name="imetadataimportgetclasslayout-method"></a>IMetaDataImport::GetClassLayout メソッド

指定した TypeDef トークンによって参照されるクラスのレイアウト情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `td`  
 から返されるレイアウトを持つクラスの TypeDef トークン。  
  
 `pdwPackSize`  
 入出力クラスのパックサイズを表す1、2、4、8、または16のいずれかの値。  
  
 `rFieldOffset`  
 入出力 [COR_FIELD_OFFSET](cor-field-offset-structure.md) 値の配列。  
  
 `cMax`  
 [in] `rFieldOffset` 配列の最大サイズ。  
  
 `pcFieldOffset`  
 入出力で返される要素の数 `rFieldOffset` 。  
  
 `pulClassSize`  
 入出力によって表されるクラスのサイズ (バイト単位) `td` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
