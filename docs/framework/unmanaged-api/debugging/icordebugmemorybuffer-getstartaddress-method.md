---
title: ICorDebugMemoryBuffer::GetStartAddress メソッド
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: f76bf1479db987e4956d8b876f67d629d927f956
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710762"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a>ICorDebugMemoryBuffer::GetStartAddress メソッド

メモリ バッファーの開始アドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `address`  
 [out] メモリ バッファーの開始アドレスへのポインター。  
  
## <a name="remarks"></a>注釈  
  
> [!WARNING]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMemoryBuffer インターフェイス](icordebugmemorybuffer-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
