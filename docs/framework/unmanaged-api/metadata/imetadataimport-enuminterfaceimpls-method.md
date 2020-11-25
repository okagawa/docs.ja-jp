---
title: IMetaDataImport::EnumInterfaceImpls メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 0b040a2741a44b9d361dabc38c26b8934659003b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711521"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls メソッド

指定したによって実装されているすべてのインターフェイスを列挙 `TypeDef` します。
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `phEnum`  
 [入力、出力]列挙子へのポインター。  
  
 `td`  
 からインターフェイスの実装を表す MethodDef トークンを列挙する TypeDef のトークン。  
  
 `rImpls`  
 入出力MethodDef トークンを格納するために使用される配列。  
  
 `cMax`  
 から配列の最大長 `rImpls` 。  
  
 `pcImpls`  
 入出力で返されたトークンの実際の数 `rImpls` 。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` 正常に返されました。|  
|`S_FALSE`|列挙する MethodDef トークンがありません。 この場合、 `pcImpls` は0に設定されます。|  

## <a name="remarks"></a>注釈

列挙体は `mdInterfaceImpl` 、指定したによって実装された各インターフェイスのトークンのコレクションを返し `TypeDef` ます。 インターフェイストークンは、インターフェイスが指定された順序で返され `DefineTypeDef` ます (またはを使用 `SetTypeDefProps` )。 返されたトークンのプロパティは、 `mdInterfaceImpl` [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)を使用して照会できます。
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
