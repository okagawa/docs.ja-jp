---
title: ICorDebugThread::GetUserState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
ms.openlocfilehash: dd3936656ce1c9482b7f07a5780fcf651356b4be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727966"
---
# <a name="icordebugthreadgetuserstate-method"></a>ICorDebugThread::GetUserState メソッド

このスレッドの現在のユーザー状態を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pState`  
 入出力このスレッドの現在のユーザー状態を示す CorDebugUserState 列挙値のビットごとの組み合わせへのポインター。  
  
## <a name="remarks"></a>注釈  

 スレッドのユーザー状態は、デバッグ中のプログラムによって検査されるときのスレッドの状態です。 スレッドに複数の状態ビットが設定されている可能性があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
