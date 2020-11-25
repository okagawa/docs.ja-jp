---
title: ICorDebugGuidToTypeEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: 68f548705213da7d715ae569116abae0cd24129d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705658"
---
# <a name="icordebugguidtotypeenumnext-method"></a>ICorDebugGuidToTypeEnum::Next メソッド

Guid を型情報にマップする、指定された数の [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `celt`  
 から取得する GUID から型へのマッピングオブジェクトの数。  
  
 `values`  
 入出力ポインターの配列。それぞれのポインターが [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) オブジェクトを指します。これは、Windows ランタイム GUID を対応するテキストオブジェクトにマップします。  
  
 `pceltFetched`  
 入出力実際にで返される [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) オブジェクトの数へのポインター `values` 。  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  

 **プラットフォーム:** Windows ランタイム  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugGuidToTypeEnum インターフェイス](icordebugguidtotypeenum-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
