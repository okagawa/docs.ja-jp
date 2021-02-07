---
description: '詳細については、次を参照してください: GetCachedInterfacePointers メソッド'
title: ICorDebugComObjectValue::GetCachedInterfacePointers メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
ms.openlocfilehash: 737d71f6aa903a3dfa97f583b47a322ec074147f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710856"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers メソッド

現在のランタイム呼び出し可能ラッパー (RCW) にキャッシュされている生のインターフェイスポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a>パラメーター  

 `bIInspectableOnly`  
 からメソッドが、 `IInspectable` ランタイム呼び出し可能ラッパー (RCW) によってキャッシュされた Windows ランタイムインターフェイス (インターフェイス) またはすべての COM インターフェイスだけを返すかどうかを示す値。  
  
 `celt`  
 からアドレスを取得するオブジェクトの数。  
  
 `pceltFetched`  
 入出力 `CORDB_ADDRESS` で実際に返される値の数へのポインター `ptrs` 。  
  
 `ptrs`  
 キャッシュされた `CORDB_ADDRESS` インターフェイスオブジェクトのアドレスを格納している値の配列の開始アドレスへのポインター。  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugComObjectValue のインターフェイス](icordebugcomobjectvalue-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
