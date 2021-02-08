---
description: '詳細については、次を参照してください: BreakpointSetError メソッド'
title: ICorDebugManagedCallback::BreakpointSetError メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
ms.openlocfilehash: cf78b4dc06a71b6ac0eb4f653a00c1b3c6ae464b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791089"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a>ICorDebugManagedCallback::BreakpointSetError メソッド

関数が just-in-time (JIT) コンパイルされる前に設定されたブレークポイントを共通言語ランタイムが正しくバインドできなかったことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pAppDomain`  
 からバインドされていないブレークポイントを含むアプリケーションドメインを表す、のオブジェクトへのポインター。  
  
 `pThread`  
 からバインドされていないブレークポイントを含むスレッドを表す、表示スレッドオブジェクトへのポインター。  
  
 `pBreakpoint`  
 からバインドされていないブレークポイントを表す ICorDebugBreakpoint オブジェクトへのポインター。  
  
 `dwError`  
 からエラーを示す整数。  
  
## <a name="remarks"></a>解説  

 指定されたブレークポイントはヒットしません。 デバッガーは、非アクティブ化して再バインドする必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
