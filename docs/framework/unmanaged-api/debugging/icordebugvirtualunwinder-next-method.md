---
description: '詳細情報: ICorDebugVirtualUnwinder:: Next メソッド'
title: ICorDebugVirtualUnwinder::Next メソッド
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: b509e8e4fb24c66764999e67ba7e36299ce7f570
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790517"
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
