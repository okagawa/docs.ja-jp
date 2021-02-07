---
description: '詳細について: ICorDebugProcess6::P rocessStateChanged メソッド'
title: ICorDebugProcess6::ProcessStateChanged メソッド
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 8060c29598adf5d4bbe7bffb4cd6611ee19a2669
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691368"
---
# <a name="icordebugprocess6processstatechanged-method"></a>ICorDebugProcess6::ProcessStateChanged メソッド

プロセスが実行されていることを [ICorDebug](icordebug-interface.md) に通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a>パラメーター  

 `change`  
 から [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) 列挙型のメンバー  
  
## <a name="remarks"></a>解説  

 デバッガーはこのメソッドを呼び出して、プロセスが実行されていることを [ICorDebug](icordebug-interface.md) に通知します。  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess6 インターフェイス](icordebugprocess6-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
