---
description: '詳細については、次を参照してください: IMetaDataImport:: Enummethod Withname メソッド'
title: IMetaDataImport::EnumMethodsWithName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: b77fc15bd7752b5b6b2b95d66a6bf04518616884
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745607"
---
# <a name="imetadataimportenummethodswithname-method"></a>IMetaDataImport::EnumMethodsWithName メソッド

指定された名前を持ち、指定された TypeDef トークンによって参照される型で定義されているメソッドを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `phEnum`  
 [入力、出力]列挙子へのポインター。 このメソッドの最初の呼び出しでは、この値は NULL である必要があります。  
  
 `cl`  
 から列挙するメソッドを持つ型を表す TypeDef トークン。  
  
 `szName`  
 から列挙型のスコープを制限する名前。  
  
 `rMethods`  
 入出力MethodDef トークンを格納するために使用される配列。  
  
 `cMax`  
 [in] `rMethods` 配列の最大サイズ。  
  
 `pcTokens`  
 入出力で返される MethodDef トークンの数 `rMethods` 。  
  
## <a name="remarks"></a>解説  

 このメソッドは、フィールドとメソッドを列挙しますが、プロパティやイベントは列挙しません。 [IMetaDataImport:: enummethods](imetadataimport-enummethods-method.md)とは異なり、は、 `EnumMethodsWithName` 指定された名前を持たないすべてのメソッドトークンを破棄します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName` 正常に返されました。|  
|`S_FALSE`|列挙するトークンがありません。 この場合、 `pcTokens` は0になります。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
