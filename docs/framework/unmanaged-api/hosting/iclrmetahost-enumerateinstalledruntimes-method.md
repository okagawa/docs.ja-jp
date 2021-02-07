---
description: '詳細について: ICLRMetaHost:: EnumerateInstalledRuntimes メソッド'
title: ICLRMetaHost::EnumerateInstalledRuntimes メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
ms.openlocfilehash: a1c2fe46a64339e013df0f65dc073d183036a0fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689197"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a>ICLRMetaHost::EnumerateInstalledRuntimes メソッド

コンピューターにインストールされている共通言語ランタイム (CLR) の各バージョンの有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを含む列挙を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppEnumerator`  
 入出力コンピューターにインストールされている CLR の各バージョンに対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスの列挙体。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`ppEnumerator` が null です。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRMetaHost インターフェイス](iclrmetahost-interface.md)
- [ホスティング](index.md)
