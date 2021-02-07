---
description: '詳細について: ICorDebug:: SetManagedHandler メソッド'
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
ms.openlocfilehash: 5817bd39a2c4e7c71dc12ca8d2d9b1263d116ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754356"
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
  
## <a name="remarks"></a>解説  

 `SetManagedHandler` 作成時にを呼び出す必要があります。  
  
 の実装に、デバッグ `ICorDebugManagedCallback` 対象のアプリケーションのデバッグイベントを処理するための十分なインターフェイスが含まれていない場合は、 `SetManagedHandler` E_NOINTERFACE の HRESULT が返されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](icordebug-interface.md)
