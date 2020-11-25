---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes メソッド
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: b52614065d599edf8e556524c33e8bc50b4924ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709181"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a>ICorDebugSymbolProvider::GetAssemblyImageBytes メソッド

マージされたアセンブリ内の指定の相対仮想アドレス (RVA: relative virtual address) で、マージされたアセンブリのデータを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `rva`  
 [in] マージされたアセンブリ内の相対仮想アドレス (RVA)。  
  
 `length`  
 マージされたアセンブリから読み取るバイト数。  
  
 `ppMemoryBuffer`  
 マージされたアセンブリメタデータを持つメモリバッファーに関する情報を格納している、 [のオブジェクトの](icordebugmemorybuffer-interface.md) アドレスへのポインター。  
  
## <a name="remarks"></a>注釈  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugSymbolProvider インターフェイス](icordebugsymbolprovider-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
