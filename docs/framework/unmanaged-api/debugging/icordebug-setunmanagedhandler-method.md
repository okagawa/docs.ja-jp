---
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
ms.openlocfilehash: 0bce14a6853c872d27057b9fffc32b54c59abf13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723390"
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
  
## <a name="remarks"></a>注釈  

 アンマネージイベントのイベントハンドラーオブジェクトは、 [ICorDebug:: Initialize](icordebug-initialize-method.md) の呼び出しの後、 [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) または [ICorDebug::D e](icordebug-debugactiveprocess-method.md)の呼び出しの前に設定する必要があります。 ただし、従来の目的では、最初のネイティブデバッグイベントが発生するまで、アンマネージイベントのイベントハンドラーオブジェクトを設定する必要はありません。 具体的には、で CREATE_SUSPENDED フラグが設定されている場合、 `ICorDebug::CreateProcess` メインスレッドが再開されるまでネイティブデバッグイベントをディスパッチできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](icordebug-interface.md)
