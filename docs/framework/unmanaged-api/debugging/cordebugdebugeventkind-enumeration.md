---
description: 詳細については、「CorDebugDebugEventKind 列挙型」を参照してください。
title: CorDebugDebugEventKind 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
ms.openlocfilehash: 62094c934873a74fdab01fad87c42126e28cb0f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801710"
---
# <a name="cordebugdebugeventkind-enumeration"></a>CorDebugDebugEventKind 列挙体

[DecodeEvent](icordebugprocess6-decodeevent-method.md)メソッドによって情報がデコードされるイベントの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|モジュールの読み込みイベント。|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|モジュールのアンロード イベント。|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|初回例外。|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|ユーザーの初回例外。|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|`catch` ハンドラーが存在する例外。|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|未処理の例外。|  
  
## <a name="remarks"></a>解説  

 この列挙体のメンバーは、 `CorDebugDebugEventKind` によっては、の [イベント:: GetEventKind](icordebugdebugevent-geteventkind-method.md) メソッドを呼び出すことによって返されます。  
  
> [!NOTE]
> この列挙型は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
