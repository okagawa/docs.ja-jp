---
title: ICorDebugExceptionObjectCallStackEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: 17d5367564ec1ec98efc264ad9a5794c0d04a947
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672137"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a>ICorDebugExceptionObjectCallStackEnum::Next メソッド

例外オブジェクトの呼び出し履歴の情報を格納している、指定した数の [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `celt`  
 から取得する [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) インスタンスの数。  
  
 `values`  
 入出力ポインターの配列。それぞれが [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) オブジェクトを指します。  
  
 `pceltFetched`  
 入出力実際に返された [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) インスタンスの数へのポインター。  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugExceptionObjectCallStackEnum インターフェイス](icordebugexceptionobjectcallstackenum-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
