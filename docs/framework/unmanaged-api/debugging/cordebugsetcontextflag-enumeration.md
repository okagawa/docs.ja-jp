---
title: CorDebugSetContextFlag 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
ms.openlocfilehash: 078dfefc70704eaadb9cf3c06cfe58f276f7dfce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726030"
---
# <a name="cordebugsetcontextflag-enumeration"></a>CorDebugSetContextFlag 列挙体

スタック上のアクティブ (またはリーフ) フレーム上からのコンテキストなのか、別のフレームからのアンワインドにより計算されたコンテキストなのかを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|SET_CONTEXT_FLAG_ACTIVE_FRAME|コンテキストは、スレッドのアクティブなコンテキストです。|  
|SET_CONTEXT_FLAG_UNWIND_FRAME|コンテキストは、別のフレームからのアンワインドによって計算されています。|  
  
## <a name="remarks"></a>注釈  

 `CorDebugSetContextFlag` によって使用される値を提供する、には、「 [SetContext](icordebugstackwalk-setcontext-method.md) メソッドです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
- [デバッグ](index.md)
