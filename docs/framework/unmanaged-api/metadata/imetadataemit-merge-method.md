---
description: '詳細情報: IMetaDataEmit:: Merge メソッド'
title: IMetaDataEmit::Merge メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 6b78dd20555acf1eaf610ed05d8a37ab6cdeee5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745945"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge メソッド

マージするスコープの一覧に、指定したインポートされたスコープを追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pImport`  
 からマージするインポートされたスコープを識別する [IMetaDataImport](imetadataimport-interface.md) オブジェクトへのポインター。  
  
 `pIMap`  
 からトークンの再マップを指定する [IMapToken](imaptoken-interface.md) オブジェクトへのポインター。  
  
 `pHandler`  
 からエラーを指定する [IUnknown](/cpp/atl/iunknown) オブジェクトへのポインター。  
  
## <a name="remarks"></a>解説  

 [IMetaDataEmit:: MergeEnd](imetadataemit-mergeend-method.md)を呼び出して、メタデータの1つのスコープへのマージをトリガーします。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
