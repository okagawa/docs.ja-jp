---
description: '詳細について: IMetaDataAssemblyImport:: GetFileProps メソッド'
title: IMetaDataAssemblyImport::GetFileProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: 6814fee7edf5478a1ce2cf2b81d8f16fa62cd3f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784107"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps メソッド

指定したメタデータシグネチャを持つファイルのプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `mdf`  
 から `mdFile` プロパティを取得する対象のファイルを表すメタデータトークン。  
  
 `szName`  
 入出力ファイルの簡易名。  
  
 `cchName`  
 からのサイズ (ワイド文字数) `szName` 。  
  
 `pchName`  
 入出力実際にで返されるワイド文字数 `szName` 。  
  
 `ppbHashValue`  
 入出力ハッシュ値へのポインター。 これは、ファイルの SHA-1 アルゴリズムを使用したハッシュです。  
  
 `pcbHashValue`  
 入出力返されたハッシュ値のワイド文字の数。  
  
 `pdwFileFlags`  
 入出力ファイルに適用されるメタデータを記述するフラグへのポインター。 Flags 値は、1つまたは複数の [Corfileflags](corfileflags-enumeration.md) 値を組み合わせたものです。  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](imetadataassemblyimport-interface.md)
