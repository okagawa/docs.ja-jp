---
description: 詳細については、「ICorDebugManagedCallback3 インターフェイス」を参照してください。
title: ICorDebugManagedCallback3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: 9fb3d44b1d793935ac997e8e4d8d86de4466f7b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801190"
---
# <a name="icordebugmanagedcallback3-interface"></a>ICorDebugManagedCallback3 インターフェイス

有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CustomNotification メソッド](icordebugmanagedcallback3-customnotification-method.md)|有効なカスタムデバッガー通知が発生したことを示します。|  
  
## <a name="remarks"></a>解説  

 このインターフェイスは、" [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) [" というインターフェイスを論理的](icordebugmanagedcallback-interface.md)に拡張したものです。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
- [ICorDebugManagedCallback2 インターフェイス](icordebugmanagedcallback2-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
