---
title: IMetaDataAssemblyImport::GetAssemblyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: 1e1a86cdf55812197aae653dca256fb910a7f168
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733894"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps メソッド

指定したメタデータシグネチャを持つアセンブリのプロパティのセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `mda`  
 [入力]。 `mdAssembly`プロパティを取得する対象のアセンブリを表すメタデータトークン。  
  
 `ppbPublicKey`  
 入出力公開キーまたはメタデータトークンへのポインター。  
  
 `pcbPublicKey`  
 入出力返される公開キーのバイト数。  
  
 `pulHashAlgId`  
 入出力アセンブリ内のファイルのハッシュに使用されるアルゴリズムへのポインター。  
  
 `szName`  
 入出力アセンブリの簡易名。  
  
 `cchName`  
 からのサイズ (ワイド文字数) `szName` 。  
  
 `pchName`  
 入出力実際にで返されるワイド文字数 `szName` 。  
  
 `pMetaData`  
 入出力アセンブリメタデータを格納している ASSEMBLYMETADATA 構造体へのポインター。  
  
 `pdwAssemblyFlags`  
 入出力アセンブリに適用されるメタデータを記述するフラグ。 この値は、1つまたは複数の [Corassemblyflags](corassemblyflags-enumeration.md) 値を組み合わせたものです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](imetadataassemblyimport-interface.md)
