---
title: ICorDebugVirtualUnwinder::Next メソッド
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 55f10a6148f0b11cf74492afe947d5921a1d1458
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396425"
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder::Next メソッド
呼び出し元のコンテキストに進みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a>パラメーター  
 [なし] :  
  
## <a name="return-value"></a>戻り値  
 アンワインドが正常に発生した場合は `S_OK`、フレームがないためにアンワインドが完了できなかった場合は `CORDBG_S_AT_END_OF_STACK`。  
  
 失敗を示す HRESULT が返される場合、ICorDebug API は `CORDBG_E_DATA_TARGET_ERROR` を返します。  
  
## <a name="remarks"></a>解説  
 スタック ウォーカーにより、前へ進んでいることが確認されます。これにより、最終的に `Next` の呼び出しによって、失敗を示す HRESULT または `CORDBG_S_AT_END_OF_STACK` が返されます。 無制限 `S_OK` に戻ると、無限ループが発生する可能性があります。  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMemoryBuffer インターフェイス](icordebugmemorybuffer-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
