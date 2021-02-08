---
description: '詳細について: ICorDebugVariableSymbol:: GetSize メソッド'
title: ICorDebugVariableSymbol::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: f4098bf5e053ab66dd7966d4b665cfad4dee01d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790582"
---
# <a name="icordebugvariablesymbolgetsize-method"></a>ICorDebugVariableSymbol::GetSize メソッド

変数のサイズ (バイト単位) を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pcbValue`  
 変数のサイズが格納されている 32 ビットの符号なし整数へのポインター。  
  
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
