---
description: '詳細について: ICorDebugManagedCallback2::D estroyConnection メソッド'
title: ICorDebugManagedCallback2::DestroyConnection メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
ms.openlocfilehash: f17def5599dc02ed6b7b49d7f8ed4db02eb40181
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790894"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a>ICorDebugManagedCallback2::DestroyConnection メソッド

指定された接続が終了したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pProcess`  
 から破棄された接続を含むプロセスを表す、のオブジェクトへのポインター。  
  
 `dwConnectionId`  
 から破棄された接続の ID。  
  
## <a name="remarks"></a>解説  

 ホストがホスト `DestroyConnection` [API](../hosting/index.md)で[ICLRDebugManager:: endconnection](../hosting/iclrdebugmanager-endconnection-method.md)を呼び出すと、コールバックが発生します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback2 インターフェイス](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
