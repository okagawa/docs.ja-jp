---
title: ICorDebugThread2::InterceptCurrentException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: 96e3a90bcb7700915bfd3618d7bae40c0ff64a75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678598"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a>ICorDebugThread2::InterceptCurrentException メソッド

デバッガーがこのスレッドの現在の例外をインターセプトできるようにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pFrame`  
 からアクティブなスタックフレームを表すテキストフレームへのポインター。  
  
## <a name="remarks"></a>注釈  

 メソッドは、 `InterceptCurrentException` 例外コールバック ( [ICorDebugManagedCallback2:: exception](icordebugmanagedcallback2-exception-method.md)) と、それに関連付けられています: [: Continue](icordebugcontroller-continue-method.md)への呼び出しの間で呼び出すことができます。[ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md)  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
