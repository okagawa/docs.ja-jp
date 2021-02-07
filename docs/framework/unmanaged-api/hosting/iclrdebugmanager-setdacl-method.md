---
description: '詳細情報: ICLRDebugManager:: SetDacl メソッド'
title: ICLRDebugManager::SetDacl メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetDacl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetDacl
helpviewer_keywords:
- SetDacl method [.NET Framework hosting]
- ICLRDebugManager::SetDacl method [.NET Framework hosting]
ms.assetid: 52f4af3f-e02b-4c20-9fd9-e8e4f4d6fc31
topic_type:
- apiref
ms.openlocfilehash: b507d94f9e23e509d279a0fd4e32c8c996a4668b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689574"
---
# <a name="iclrdebugmanagersetdacl-method"></a>ICLRDebugManager::SetDacl メソッド

このメソッドは実装されていません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetDacl (  
    [in] PACL pacl  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pacl`  
 からAccess Control リスト (ACL) へのポインター。  
  
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
- [GetDacl メソッド](iclrdebugmanager-getdacl-method.md)
- [IHostControl インターフェイス](ihostcontrol-interface.md)
