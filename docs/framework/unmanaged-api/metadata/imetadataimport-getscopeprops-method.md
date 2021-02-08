---
description: '詳細について: IMetaDataImport:: GetScopeProps メソッド'
title: IMetaDataImport::GetScopeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 2ed7c08cc876f467a46fe38c7c27719e5608e623
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789152"
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps メソッド

現在のメタデータ スコープにあるアセンブリまたはモジュールの名前、およびオプションでバージョン ID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szName`  
 入出力アセンブリ名またはモジュール名のバッファー。  
  
 `cchName`  
 からのワイド文字のサイズ `szName` 。  
  
 `pchName`  
 入出力で返されたワイド文字の数 `szName` 。  
  
 `pmvid`  
 [out、省略可能]アセンブリまたはモジュールのバージョンを一意に識別する GUID へのポインター。  
  
## <a name="remarks"></a>解説  

 これらのプロパティを設定するには、 [IMetaDataEmit:: SetModuleProps](imetadataemit-setmoduleprops-method.md) メソッドを使用します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
