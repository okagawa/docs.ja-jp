---
description: '詳細については、次の情報を参照してください: の説明:: の例外メソッド'
title: ICorDebugManagedCallback::Exception メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
ms.openlocfilehash: f738c328e1f6edfeb61a1d5e2ba8f9dd827d05dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790972"
---
# <a name="icordebugmanagedcallbackexception-method"></a>ICorDebugManagedCallback::Exception メソッド

マネージコードから例外がスローされたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pAppDomain`  
 から例外がスローされたアプリケーションドメインを表す、のオブジェクトへのポインター。  
  
 `pThread`  
 から例外がスローされたスレッドを表す、スレッドオブジェクトへのポインター。  
  
 `unhandled`  
 からこの値がの場合、 `false` アプリケーションによって例外がまだ処理されていません。それ以外の場合、例外はハンドルされず、プロセスを終了します。  
  
## <a name="remarks"></a>解説  

 スレッドオブジェクトから特定の例外を取得できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
