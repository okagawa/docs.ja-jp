---
title: IMetaDataAssemblyImport::FindManifestResourceByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
ms.openlocfilehash: 152f62fddee3eaa7fa14e454e6eb7ea2547265ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731580"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a>IMetaDataAssemblyImport::FindManifestResourceByName メソッド

指定した名前のマニフェストリソースへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a>パラメーター  

 `szName`  
 からリソースの名前。  
  
 `ptkManifestResource`  
 入出力メタデータトークンを格納するために使用される配列 `mdManifestResource` 。それぞれがマニフェストリソースを表します。  
  
## <a name="remarks"></a>注釈  

 メソッドは、 `FindManifestResourceByName` 参照を解決するために共通言語ランタイムによって採用されている標準の規則を使用します。  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](imetadataassemblyimport-interface.md)
- [ランタイムがアセンブリを検索する方法](../../deployment/how-the-runtime-locates-assemblies.md)
