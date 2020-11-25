---
title: ICorDebugModuleDebugEvent::GetModule メソッド
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: ec23cda02ff689a3365fe96fb5280054a9795caa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709506"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a>ICorDebugModuleDebugEvent::GetModule メソッド

ロードまたはアンロードされたばかりのマージ モジュールを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppModule`  
 [out] ロードまたはアンロードされたばかりのマージ モジュールを表す ICorDebugModule オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 [Geteventkind](icordebugdebugevent-geteventkind-method.md)メソッドを呼び出して、モジュールが読み込まれたかアンロードされたかを確認できます。  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugModuleDebugEvent インターフェイス](icordebugmoduledebugevent-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
