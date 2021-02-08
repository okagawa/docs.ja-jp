---
description: '詳細について: IMetaDataAssemblyImport:: GetExportedTypeProps メソッド'
title: IMetaDataAssemblyImport::GetExportedTypeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 894fb65fb6de76a218489b2a85a2d3c20c572789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784120"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps メソッド

指定したメタデータシグネチャを持つ、エクスポートされた型のプロパティのセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,
    [out] LPWSTR            szName,
    [in]  ULONG             cchName,
    [out] ULONG             *pchName,
    [out] mdToken           *ptkImplementation,
    [out] mdTypeDef         *ptkTypeDef,
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `mdct`  
 からエクスポートされた `mdExportedType` 型を表すメタデータトークン。  
  
 `szName`  
 入出力エクスポートされた型の名前。  
  
 `cchName`  
 からのサイズ (ワイド文字単位) `szName` 。  
  
 `pchName`  
 入出力実際に返されるワイド文字の数 `szName`  
  
 `ptkImplementation`  
 入出力 `mdFile` `mdAssemblyRef` エクスポートされた `mdExportedType` 型のプロパティへのアクセスを格納または許可する、、、またはメタデータトークン。  
  
 `ptkTypeDef`  
 入出力 `mdTypeDef` ファイル内の型を表すトークンへのポインター。  
  
 `pdwExportedTypeFlags`  
 入出力エクスポートされた型に適用されるメタデータを記述するフラグへのポインター。 Flags 値には、1つまたは複数の [Cortypeattr](cortypeattr-enumeration.md) 値を指定できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](imetadataassemblyimport-interface.md)
