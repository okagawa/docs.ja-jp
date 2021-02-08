---
description: '詳細について: ICorDebugAssembly3:: GetContainerAssembly メソッド'
title: ICorDebugAssembly3::GetContainerAssembly メソッド
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 5a6bc6dfb1c8403137a9444ff1cc4f64e75da65d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791518"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly メソッド

この `ICorDebugAssembly3` オブジェクトのコンテナー アセンブリを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppAssembly`  
 コンテナーアセンブリを表す、オブジェクトのアドレスへのポインター。メソッドの呼び出しが失敗した場合は **null** 。  
  
## <a name="return-value"></a>戻り値  

 `S_OK` メソッドの呼び出しが成功した場合は。それ以外の場合、 `S_FALSE` 、、および `ppAssembly` は **null** になります。  
  
## <a name="remarks"></a>解説  

 このアセンブリが 1 つのコンテナー アセンブリ内の他のアセンブリとマージされている場合、このメソッドはコンテナー アセンブリを返します。 詳細と用語については、「 [ICorDebugProcess6:: EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) 」を参照してください。  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugAssembly3 インターフェイス](icordebugassembly3-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
