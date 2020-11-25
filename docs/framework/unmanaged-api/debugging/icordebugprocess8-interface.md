---
title: ICorDebugProcess8 インターフェイス
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
ms.openlocfilehash: 00c432374eeb82692492b8e6b10472f13bc44d6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732516"
---
# <a name="icordebugprocess8-interface"></a>ICorDebugProcess8 インターフェイス

[.NET Framework 4.6 以降のバージョンでサポートされています]  
  
 ICorDebugManagedCallback2 Process インターフェイスを論理的に拡張して、特定の種類の[ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)例外コールバックを有効または無効にします。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnableExceptionCallbacksOutsideOfMyCode メソッド](icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|特定の種類の [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外コールバックを有効または無効にします。|  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
