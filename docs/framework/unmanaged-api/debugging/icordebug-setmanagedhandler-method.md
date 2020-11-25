---
title: ICorDebug::SetManagedHandler メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 97a4a464d3dfb7b333f44ac4206bd880fd171e16
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723416"
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler メソッド

マネージイベントのイベントハンドラーオブジェクトを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pCallback`  
 からイベントハンドラーオブジェクトである、ツール [コールバック](icordebugmanagedcallback-interface.md) オブジェクトへのポインター。  
  
## <a name="remarks"></a>注釈  

 `SetManagedHandler` 作成時にを呼び出す必要があります。  
  
 の実装に、デバッグ `ICorDebugManagedCallback` 対象のアプリケーションのデバッグイベントを処理するための十分なインターフェイスが含まれていない場合は、 `SetManagedHandler` E_NOINTERFACE の HRESULT が返されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](icordebug-interface.md)
