---
title: ICorDebugDebugEvent::GetEventKind メソッド
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 7876dc6ec5ecee52b64e54e1c42533f8348e4dc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713679"
---
# <a name="icordebugdebugeventgeteventkind-method"></a>ICorDebugDebugEvent::GetEventKind メソッド

この `ICorDebugDebugEvent` オブジェクトが表すイベントの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 pDebugEventKind  
 イベントの種類を示す [Cordebugdebugeventkind](cordebugdebugeventkind-enumeration.md) 列挙体メンバーへのポインター。  
  
## <a name="remarks"></a>注釈  

 `pDebugEventKind` の値に基づいて、`QueryInterface` を呼び出して、追加データを含むより正確なデバッグ イベント インターフェイスを取得できます。  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugDebugEvent インターフェイス](icordebugdebugevent-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
