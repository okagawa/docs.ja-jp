---
title: ICorDebugController::SetAllThreadsDebugState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: d8375948be5820aaf6e879b82bcfde6471cccf3f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679898"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState メソッド

プロセス内のすべてのマネージスレッドのデバッグ状態を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `state`  
 からデバッグ用のスレッドの状態を指定する "CorDebugThreadState" 列挙の値。  
  
 `pExceptThisThread`  
 からデバッグ状態設定から除外されるスレッドを表す "のスレッド" オブジェクトへのポインター。 この値が null の場合、スレッドは除外されません。  
  
## <a name="remarks"></a>注釈  

 メソッドは、 `SetAllThreadsDebugState` [EnumerateThreads メソッド](icordebugcontroller-enumeratethreads-method.md)によって表示されないスレッドに影響を与える可能性があります。そのため、メソッドを使用して中断されたスレッド `SetAllThreadsDebugState` は、メソッドを使用して再開する必要があり `SetAllThreadsDebugState` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
