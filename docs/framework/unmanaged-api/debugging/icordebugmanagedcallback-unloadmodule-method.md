---
description: '詳細については、次を参照してください: UnloadModule メソッド'
title: ICorDebugManagedCallback::UnloadModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: d8d37b28d7a7d11000c259f1bcde3138634b2498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754057"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a>ICorDebugManagedCallback::UnloadModule メソッド

共通言語ランタイムモジュール (DLL) がアンロードされたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pAppDomain`  
 からモジュールを含んでいるアプリケーションドメインを表す、のオブジェクトへのポインター。  
  
 `pModule`  
 からモジュールを表す、のモジュールオブジェクトへのポインター。  
  
## <a name="remarks"></a>解説  

 この呼び出しの後にモジュールを使用することはできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [LoadModule メソッド](icordebugmanagedcallback-loadmodule-method.md)
- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
