---
description: 詳細については、「ebuggerError メソッド」を参照してください:D。
title: ICorDebugManagedCallback::DebuggerError メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
ms.openlocfilehash: 2f73e07711f7d2ce865aab8f90862563e767fd16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791005"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError メソッド

共通言語ランタイム (CLR) からのイベントを処理しようとしたときに、エラーが発生したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pProcess`  
 からイベントが発生したプロセスを表す "いいプロセス" オブジェクトへのポインター。  
  
 `errorHR`  
 からイベントハンドラーから返された HRESULT 値。  
  
 `errorCode`  
 からCLR エラーを示す整数です。  
  
## <a name="remarks"></a>解説  

 プロセスは、エラーの性質によっては、パススルーモードに配置される場合があります。  
  
 `DebugError`コールバックは、エラーが原因でデバッグサービスが無効になっていることを示しているため、デバッガーはエラーメッセージをユーザーに対して使用できるようにする必要があります。 [GetID:](icordebugprocess-getid-method.md) : ICorDebug は安全に呼び出すことができますが、他のすべてのメソッド ( [:: Terminate](icordebug-terminate-method.md)を含む) は呼び出さないでください。 デバッガーでは、プロセスを終了するためにオペレーティングシステムの機能を使用する必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
