---
title: GetCachePath 関数
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
ms.openlocfilehash: c22f0701cfda4523f595366a97435ef8da08b0cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724469"
---
# <a name="getcachepath-function"></a>GetCachePath 関数

指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwCacheFlags`  
 からキャッシュされたアセンブリのソースを示す [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) 値。  
  
 `pwzCachePath`  
 入出力パスへの返されたポインター。  
  
 `pcchPath`  
 [入力、出力]要求された最大長 `pwzCachePath` 。戻り値は、の実際の長さ `pwzCachePath` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ASM_CACHE_FLAGS 列挙型](asm-cache-flags-enumeration.md)
- [Fusion グローバル静的関数](fusion-global-static-functions.md)
