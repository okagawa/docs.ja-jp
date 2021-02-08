---
description: '詳細情報: COR_DEBUG_STEP_RANGE 構造'
title: COR_DEBUG_STEP_RANGE 構造体
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
ms.openlocfilehash: 40462be4b165351b3265fa0833d19f18e0fa3a37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801840"
---
# <a name="cor_debug_step_range-structure"></a>COR_DEBUG_STEP_RANGE 構造体

コードの範囲に関するオフセット情報が含まれます。  
  
 この構造体は、 [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) メソッドによって使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`startOffset`|範囲の先頭のオフセット。|  
|`endOffset`|範囲の末尾のオフセット。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug .idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StepRange メソッド](icordebugstepper-steprange-method.md)
- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
