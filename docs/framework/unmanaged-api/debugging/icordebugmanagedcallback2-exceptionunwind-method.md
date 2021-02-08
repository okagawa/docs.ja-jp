---
description: '詳細情報: ICorDebugManagedCallback2:: ExceptionUnwind ワインドメソッド'
title: ICorDebugManagedCallback2::ExceptionUnwind メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: 2d98fb21cdbb0db25a11761ac9b00e99e1526cc0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790848"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind メソッド

例外アンワインド処理中の状態通知を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pAppDomain`  
 から例外がスローされたスレッドを含むアプリケーションドメインを表す、のオブジェクトへのポインター。  
  
 `pThread`  
 から例外がスローされたスレッドを表す、スレッドオブジェクトへのポインター。  
  
 `dwEventType`  
 からアンワインドフェーズ中にコールバックによって通知されるイベントを指定する CorDebugExceptionUnwindCallbackType 列挙体の値。  
  
 `dwFlags`  
 から例外に関する追加情報を指定する [Cordebugexceptionflags](cordebugexceptionflags-enumeration.md) 列挙体の値。  
  
## <a name="remarks"></a>解説  

 `ExceptionUnwind` は、例外処理プロセスのアンワインドフェーズ中にさまざまなポイントで呼び出されます。 `ExceptionUnwind` 1つの例外をアンワインドしている間に、複数回呼び出すことができます。  
  
 が `dwEventType` DEBUG_EXCEPTION_INTERCEPTED の場合、命令ポインターは、例外の原因となった命令の前 (これは複数の命令になることがあります) に、スレッドのリーフフレームに配置されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback2 インターフェイス](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
