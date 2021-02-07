---
description: '詳細について: ICorDebug:: SetUnmanagedHandler メソッド'
title: ICorDebug::SetUnmanagedHandler メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: ffd4eb7ff0056a2468ec53eb3534434c2c8d556a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754317"
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler メソッド

アンマネージイベントのイベントハンドラーオブジェクトを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pCallback`  
 からアンマネージイベントのイベントハンドラーを表す [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) オブジェクトへのポインター。  
  
## <a name="remarks"></a>解説  

 アンマネージイベントのイベントハンドラーオブジェクトは、 [ICorDebug:: Initialize](icordebug-initialize-method.md) の呼び出しの後、 [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) または [ICorDebug::D e](icordebug-debugactiveprocess-method.md)の呼び出しの前に設定する必要があります。 ただし、従来の目的では、最初のネイティブデバッグイベントが発生するまで、アンマネージイベントのイベントハンドラーオブジェクトを設定する必要はありません。 具体的には、で CREATE_SUSPENDED フラグが設定されている場合、 `ICorDebug::CreateProcess` メインスレッドが再開されるまでネイティブデバッグイベントをディスパッチできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](icordebug-interface.md)
