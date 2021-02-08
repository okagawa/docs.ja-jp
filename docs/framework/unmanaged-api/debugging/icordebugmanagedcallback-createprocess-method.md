---
description: 詳細については、次を参照
title: ICorDebugManagedCallback::CreateProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
ms.openlocfilehash: 564c9862dd90431f0626204fdfe49e59b85a124d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791050"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a>ICorDebugManagedCallback::CreateProcess メソッド

プロセスが初めてアタッチまたは開始されたときにデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pProcess`  
 からアタッチまたは開始されたプロセスを表す、のオブジェクトへのポインター。  
  
## <a name="remarks"></a>解説  

 このメソッドは、共通言語ランタイムが初期化されるまで呼び出されません。 ほとんどの [ICorDebug](icordebug-interface.md) メソッドは、コールバックの前に CORDBG_E_NOTREADY を返し `CreateProcess` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
