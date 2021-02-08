---
description: '詳細情報: ICorDebugVariableSymbol:: GetValue メソッド'
title: ICorDebugVariableSymbol::GetValue メソッド
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: ccd7eae5cc4740e83d0210a903ba0e7778aa8896
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790569"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol::GetValue メソッド

変数の値をバイト配列として取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `offset`  
 [in] 値を読み取る変数内の開始オフセットです。 このパラメーターは、オブジェクトのメンバー フィールドを読み取る際に使用されます。  
  
 `cbContext`  
 [in] `context` 引数のバイト単位のサイズ。  
  
 `context`  
 [in] 値の読み取りに使用されるスレッド コンテキスト。  
  
 `cbValue`  
 [in] `pValue` バッファーのバイト単位のサイズ。  
  
 `pcbValue`  
 [out] `pValue` バッファーに実際に書き込まれたバイト数。  
  
 `pValue`  
 [out] 変数の値が格納されているバイト配列。  
  
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
