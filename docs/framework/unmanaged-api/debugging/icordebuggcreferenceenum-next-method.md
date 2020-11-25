---
title: ICorDebugGCReferenceEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: e55c53b9610dcadee92ba9871bf52e3dacb5796b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726237"
---
# <a name="icordebuggcreferenceenumnext-method"></a>ICorDebugGCReferenceEnum::Next メソッド

ガベージコレクトされるオブジェクトに関する情報を格納している、指定した数の [COR_GC_REFERENCE](cor-gc-reference-structure.md) インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 celt  
 から取得するルートの数。  
  
 ca  
 入出力ポインターの配列。各ポインターは、ガベージコレクトされるオブジェクトのルートを表す [COR_GC_REFERENCE](cor-gc-reference-structure.md) オブジェクトを指します。  
  
 pceltFetched  
 入出力実際にで返される [COR_GC_REFERENCE](cor-gc-reference-structure.md) オブジェクトの数へのポインター `roots` 。 `celt` が 1 の場合、この値は`null` になることがあります。  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugGCReferenceEnum インターフェイス](icordebuggcreferenceenum-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
