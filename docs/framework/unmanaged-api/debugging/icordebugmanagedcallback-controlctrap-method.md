---
description: '詳細については、次を参照してください: を参照'
title: ICorDebugManagedCallback::ControlCTrap メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: 9fa71dacb20ff6df21d8aabb687c2601f27643c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791068"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a>ICorDebugManagedCallback::ControlCTrap メソッド

デバッグ対象のプロセスで CTRL + C がトラップされることをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pProcess`  
 からCTRL + C キーがトラップされるプロセスを表す、のオブジェクトへのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|デバッガーは CTRL + C トラップを処理します。|  
|S_FALSE|デバッガーは CTRL + C トラップを処理しません。|  
  
## <a name="remarks"></a>解説  

 プロセス内のすべてのアプリケーションドメインがこのコールバックに対して停止されています。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
