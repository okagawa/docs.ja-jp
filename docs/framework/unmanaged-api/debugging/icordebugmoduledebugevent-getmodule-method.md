---
description: '詳細については、次のページを参照してください: いいね。イベント:: GetModule メソッド'
title: ICorDebugModuleDebugEvent::GetModule メソッド
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: c6d7171da231576ff90f54aaefe4b473af0afd40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790738"
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
  
## <a name="remarks"></a>解説  

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
