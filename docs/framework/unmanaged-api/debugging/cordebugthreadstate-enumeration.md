---
title: CorDebugThreadState 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 5eee2aee5873fe512136bc5407e395acdc31af29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722610"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState 列挙型

デバッグのスレッドの状態を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`THREAD_RUN`|デバッグイベントが発生しない限り、スレッドは自由に実行できます。|  
|`THREAD_SUSPEND`|スレッドを実行できません。|  
  
## <a name="remarks"></a>注釈  

 デバッガーは、列挙体を使用して `CorDebugThreadState` スレッドの実行を制御します。 スレッドの状態を設定するには、次のように指定する必要があります: [: SetDebugState](icordebugthread-setdebugstate-method.md) または、モジュール [:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) メソッド。  
  
 [ホスティング API](../hosting/index.md)に提供されるコールバックによってメッセージポンプが可能になるため、中断された状態は必要ありません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
