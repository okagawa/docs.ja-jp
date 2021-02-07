---
description: '詳細について: IMetaDataImport2:: GetGenericParamProps メソッド'
title: IMetaDataImport2::GetGenericParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 06b522531282b4a30cdc8ebf001c16438e8612ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688729"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps メソッド

指定したトークンによって表されるジェネリックパラメーターに関連付けられているメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `gp`  
 からメタデータを返す対象のジェネリックパラメーターを表すトークン。  
  
 `pulParamSeq`  
 入出力 `Type` 親コンストラクターまたはメソッド内のパラメーターの序数位置。  
  
 `pdwParamFlags`  
 入出力ジェネリックパラメーターのを記述する [Corgenericparamattr](corgenericparamattr-enumeration.md) 列挙体の値 `Type` 。  
  
 `ptOwner`  
 入出力パラメーターの所有者を表す TypeDef または MethodDef トークン。  
  
 `reserved`  
 入出力将来の拡張のために予約されています。  
  
 `wzName`  
 入出力ジェネリックパラメーターの名前。  
  
 `cchName`  
 からバッファーのサイズ `wzName` 。  
  
 `pchName`  
 入出力名前の返されたサイズ (ワイド文字単位)。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
