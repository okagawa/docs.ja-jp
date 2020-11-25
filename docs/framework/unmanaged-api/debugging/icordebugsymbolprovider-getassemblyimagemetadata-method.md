---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata メソッド
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: 9644d1323660730d210bd0305c2785fce4174455
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709142"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a>ICorDebugSymbolProvider::GetAssemblyImageMetadata メソッド

マージされたアセンブリのメタデータを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppMemoryBuffer`  
 入出力マージされたアセンブリのメタデータのサイズとアドレスに関する情報を格納して [いる、のオブジェクトの](icordebugmemorybuffer-interface.md) アドレスへのポインター。  
  
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
