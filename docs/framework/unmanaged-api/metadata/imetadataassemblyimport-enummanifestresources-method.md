---
title: IMetaDataAssemblyImport::EnumManifestResources メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: c72e5b9544d1d8ae989405ac9bfdb22050b1aaaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731614"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a>IMetaDataAssemblyImport::EnumManifestResources メソッド

現在のアセンブリマニフェストで参照されているリソースの列挙子へのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a>パラメーター  

 `phEnum`  
 [入力、出力]列挙子へのポインター。 メソッドを初めて呼び出すときは、null 値を指定する必要があり `EnumManifestResources` ます。  
  
 `rManifestResources`  
 入出力メタデータトークンを格納するために使用される配列 `mdManifestResource` 。  
  
 `cMax`  
 から `mdManifestResource` に格納できるトークンの最大数 `rManifestResources` 。  
  
 `pcTokens`  
 入出力 `mdManifestResource` 実際に配置されたトークンの数 `rManifestResources` 。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumManifestResources` 正常に返されました。|  
|`S_FALSE`|列挙するトークンがありません。 この場合、 `pcTokens` は0に設定されます。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](imetadataassemblyimport-interface.md)
