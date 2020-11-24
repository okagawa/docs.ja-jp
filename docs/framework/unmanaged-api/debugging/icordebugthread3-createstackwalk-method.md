---
title: ICorDebugThread3::CreateStackWalk メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: fb9d07fffd2ec98225ce60b211f525f8dafd9725
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691070"
---
# <a name="icordebugthread3createstackwalk-method"></a>ICorDebugThread3::CreateStackWalk メソッド

スタックをアンワインドするスレッドに対し [て、このオブジェクトを](icordebugstackwalk-interface.md) 作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppStackWalk`  
 入出力スタックをアンワインドするスレッド [の、説明オブジェクトの](icordebugstackwalk-interface.md) アドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk`オブジェクトが正常に作成されました。|  
|E_FAIL|オブジェクトは作成され `ICorDebugStackWalk` ませんでした。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>解説  

 メソッドが `CreateStackWalk` 成功すると、返された `ICorDebugStackWalk` オブジェクトのコンテキストがスレッドの現在のコンテキストに設定されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
