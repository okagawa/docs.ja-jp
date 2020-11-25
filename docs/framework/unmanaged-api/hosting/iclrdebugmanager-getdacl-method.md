---
title: ICLRDebugManager::GetDacl メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.GetDacl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::GetDacl
helpviewer_keywords:
- GetDacl method [.NET Framework hosting]
- ICLRDebugManager::GetDacl method [.NET Framework hosting]
ms.assetid: 7115e920-aaff-440a-824e-39497139c6f6
topic_type:
- apiref
ms.openlocfilehash: 8a7de5a900bc1af219924b6a83f83cf7e2ef6150
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726146"
---
# <a name="iclrdebugmanagergetdacl-method"></a>ICLRDebugManager::GetDacl メソッド

このメソッドは実装されていません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDacl (  
    [out] PACL* ppacl  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppacl`  
 入出力Access Control リスト (ACL) へのインターフェイスポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|E_NOTIMPL|このメソッドは実装されていません。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRControl インターフェイス](iclrcontrol-interface.md)
- [ICLRDebugManager インターフェイス](iclrdebugmanager-interface.md)
- [SetDacl メソッド](iclrdebugmanager-setdacl-method.md)
- [IHostControl インターフェイス](ihostcontrol-interface.md)
