---
description: '詳細について: IMetaDataAssemblyImport:: GetManifestResourceProps メソッド'
title: IMetaDataAssemblyImport::GetManifestResourceProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: d8f390f8eede5153df282cc30479ceff22fb552d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728287"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps メソッド

指定されたメタデータシグネチャを持つマニフェストリソースのプロパティのセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `mdmr`  
 から `mdManifestResource` プロパティを取得する対象のリソースを表すトークン。  
  
 `szName`  
 入出力リソースの名前。  
  
 `cchName`  
 からのサイズ (ワイド文字数) `szName` 。  
  
 `pchName`  
 入出力実際にで返されるワイド文字数へのポインター `szName` 。  
  
 `ptkImplementation`  
 入出力リソースを格納し `mdFile` `mdAssemblyRef` ているファイルまたはアセンブリを表すトークンまたはトークンへのポインター。  
  
 `pdwOffset`  
 入出力ファイル内のリソースの先頭へのオフセットを指定する値へのポインター。  
  
 `pdwResourceFlags`  
 入出力リソースに適用されるメタデータを記述するフラグへのポインター。 Flags 値は、1つ以上の [Cormanifestresourceflags](cormanifestresourceflags-enumeration.md) 値を組み合わせたものです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](imetadataassemblyimport-interface.md)
