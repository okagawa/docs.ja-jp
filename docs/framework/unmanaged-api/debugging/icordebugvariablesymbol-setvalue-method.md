---
description: '詳細について: ICorDebugVariableSymbol:: SetValue メソッド'
title: ICorDebugVariableSymbol::SetValue メソッド
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: aa36712defcf44039f17fe846113c15814549e09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800852"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol::SetValue メソッド

バイト配列の値を変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `offset`  
 [in] 値を設定する変数内の開始オフセットです。 このパラメーターは、オブジェクトのメンバー フィールドに書き込む際に使用されます。  
  
 `threadID`  
 [in] 新しい値を反映させるためにコンテキストを更新する必要があるスレッドのスレッド ID。  
  
 `cbContext`  
 [in] スレッド コンテキストのバイト単位のサイズ。  
  
 `context`  
 [in] 値の書き込みに使用されるスレッド コンテキスト。  
  
 `cbValue`  
 [in] `pValue` バッファーのバイト単位のサイズ。  
  
 `pValue`  
 [in] 設定する値が含まれるバッファー。  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugVariableSymbol インターフェイス](icordebugvariablesymbol-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
