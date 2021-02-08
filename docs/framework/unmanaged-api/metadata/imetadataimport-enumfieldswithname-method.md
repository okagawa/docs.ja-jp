---
description: '詳細については、次を参照してください: IMetaDataImport:: Enumフィールド Withname メソッド'
title: IMetaDataImport::EnumFieldsWithName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: 88096b2b12a9571eb05d4550e6e26a348e28cfd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799370"
---
# <a name="imetadataimportenumfieldswithname-method"></a>IMetaDataImport::EnumFieldsWithName メソッド

指定した名前を持つ指定した型の FieldDef トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `phEnum`  
 [入力、出力]列挙子へのポインター。  
  
 `cl`  
 からフィールドを列挙する型のトークン。  
  
 `szName`  
 から列挙型のスコープを制限するフィールド名。  
  
 `rFields`  
 入出力FieldDef トークンを格納するために使用される配列。  
  
 `cMax`  
 [in] `rFields` 配列の最大サイズ。  
  
 `pcTokens`  
 入出力で返された FieldDef トークンの実際の数 `rFields` 。  
  
## <a name="remarks"></a>解説  

 [IMetaDataImport:: EnumFields](imetadataimport-enumfields-method.md)とは異なり、は `EnumFieldsWithName` 指定された名前のないすべてのフィールドトークンを破棄します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumFieldsWithName` 正常に返されました。|  
|`S_FALSE`|列挙するフィールドがありません。 この場合、 `pcTokens` は0になります。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
