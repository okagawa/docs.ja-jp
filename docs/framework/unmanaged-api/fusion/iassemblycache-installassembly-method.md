---
title: IAssemblyCache::InstallAssembly メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCache.InstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type:
- apiref
ms.openlocfilehash: 230b904dd1cca1a1289713e3df7a709bd1c3a22b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696909"
---
# <a name="iassemblycacheinstallassembly-method"></a>IAssemblyCache::InstallAssembly メソッド

指定したアセンブリをグローバルアセンブリキャッシュにインストールします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwFlags`  
 からFusion に定義されているフラグ。 サポートされている値を次に示します。  
  
- IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)  
  
- IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)  
  
 `pszManifestFilePath`  
 からインストールするアセンブリのマニフェストへのパス。  
  
 `pRefData`  
 からインストールのためのデータを格納する [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) 構造体。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IAssemblyCache インターフェイス](iassemblycache-interface.md)
