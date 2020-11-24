---
title: ICorDebugManagedCallback::LogMessage メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
ms.openlocfilehash: 92b2a7f7f1dd98f0d847119a6431e3816c16d5da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679573"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>ICorDebugManagedCallback::LogMessage メソッド

共通言語ランタイム (CLR) マネージスレッドが、 <xref:System.Diagnostics.EventLog> イベントを記録するためにクラスのメソッドを呼び出したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pAppDomain`  
 からイベントを記録したマネージスレッドを含むアプリケーションドメインを表す、コードのオブジェクトへのポインター。  
  
 `pThread`  
 からマネージスレッドを表す、コードスレッドオブジェクトへのポインター。  
  
 `lLevel`  
 からイベントログに書き込まれた説明メッセージの重大度レベルを示す、ログ記録 [Levelenum](logginglevelenum-enumeration.md) 列挙体の値。  
  
 `pLogSwitchName`  
 からトレーススイッチの名前へのポインター。  
  
 `pMessage`  
 からイベントログに書き込まれたメッセージへのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
