---
description: '詳細については、次を参照してください: ICorDebugProcess8:: Enableexception Soutsideofmycode メソッド'
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: a85c9d62e5fb62fe620f0901509afa5a03504d4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691277"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド

[.NET Framework 4.6 以降のバージョンでサポートされています]  
  
 特定の種類の [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外コールバックを有効または無効にします。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `enableExceptionsOutsideOfJMC`  
 [入力]  
  
## <a name="remarks"></a>解説  

 `enableExceptionsOutsideOfJMC` の値が `false` の場合:  
  
- デバッガーへのコールバックでは DEBUG_EXCEPTION_FIRST_CHANCE 例外は発生しません。  
  
- 例外がユーザー コードにエスケープされることがない場合 (つまり、例外の発生から例外ハンドラーへのパスで、JustMyCode または JMC とマークされているメソッドがない場合)、DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外は発生しません。  
  
 `enableExceptionsOutsideOfJMC` の既定値は `true`です。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess8 インターフェイス](icordebugprocess8-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
