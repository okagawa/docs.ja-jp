---
title: 'ICorDebugCode4:: EnumerateVariableHomes メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: 6d58efa5629bb02158a275dec61c0313bca821a1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720758"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a>ICorDebugCode4:: EnumerateVariableHomes メソッド

関数のローカル変数および引数に対する列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppEnum`  
 関数内のローカル変数および引数の列挙子である、の [型](icordebugvariablehomeenum-interface.md) のオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 "ICorDebugEnum" インターフェイスから派生した標準列挙子で[ある、表示変数](icordebugvariablehomeenum-interface.md)[ホーム](icordebugvariablehome-interface.md)オブジェクトを列挙できます。 コレクションには、同じスロットまたは引数インデックスに対して、関数内の異なるポイントに異なる [ホーム](icordebugvariablehome-interface.md) オブジェクトが含まれている場合があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugCode4 インターフェイス](icordebugcode4-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
