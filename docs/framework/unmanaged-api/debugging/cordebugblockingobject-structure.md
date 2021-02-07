---
description: '詳細については、次を参照してください: CorDebugBlockingObject 構造体'
title: CorDebugBlockingObject 構造体
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
ms.openlocfilehash: 2b16af5eecb01067c2ee6811613f964af391f345
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712220"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject 構造体

スレッドをブロックしているオブジェクトと、スレッドがブロックされている具体的な理由を定義します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`pBlockingObject`|スレッドがブロックされているオブジェクト。 このオブジェクトは、現在の同期済みの状態の間のみ有効です。 2つのスレッドが同じ同期状態内の同じオブジェクトでブロックしている場合は、 [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) メソッドで同じ値が返されることが予想されます。 ただし、インターフェイスは、同等のポインターである場合とない場合があります。|  
|`dwTimeout`|ブロッキング操作がタイムアウトするまでのミリ秒数。または、タイムアウトしないことを示す値が無限であることを示します。タイムアウト値は、残りの時間ではなく、ブロック操作の合計時間を指定します。|  
|`blockingReason`|このオブジェクトでスレッドがブロックされた理由。|  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug .idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
