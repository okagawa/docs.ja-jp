---
title: COR_ACTIVE_FUNCTION 構造体
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
ms.openlocfilehash: c50ba530d78296ebb956329b2f34b4f1e5cae94c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727420"
---
# <a name="cor_active_function-structure"></a>COR_ACTIVE_FUNCTION 構造体

スレッドのフレームで現在アクティブな機能に関する情報が含まれます。 この構造体は、 [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) メソッドによって使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`pAppDomain`|フィールドのアプリケーションドメイン所有者へのポインター `ilOffset` 。|  
|`pModule`|フィールドのモジュール所有者へのポインター `ilOffset` 。|  
|`pFunction`|フィールドの関数所有者へのポインター `ilOffset` 。|  
|`ilOffset`|フレームの MSIL (Microsoft 中間言語) オフセット。|  
|`flags`|将来の拡張のために予約されています。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug .idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
