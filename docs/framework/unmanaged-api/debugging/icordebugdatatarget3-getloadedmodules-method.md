---
title: ICorDebugDataTarget3::GetLoadedModules メソッド
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: efbada02b7a24e0a7ed613b86b8a4a1a0b5b051a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713751"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>ICorDebugDataTarget3::GetLoadedModules メソッド

これまでに読み込まれたモジュールの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cRequestedModules`  
 [in] 情報を要求する対象のモジュールの数。  
  
 `pcFetchedModules`  
 [out] 情報が返された対象モジュールの数へのポインター。  
  
 `pLoadedModules`  
 入出力読み込まれたモジュールに関する情報を提供する [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) オブジェクトの配列へのポインター。  
  
## <a name="remarks"></a>注釈  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugDataTarget3 インターフェイス](icordebugdatatarget3-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
