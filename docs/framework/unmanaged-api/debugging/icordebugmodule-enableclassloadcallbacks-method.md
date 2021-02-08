---
description: '詳細については、「EnableClassLoadCallbacks Module:: メソッド」を参照してください。'
title: ICorDebugModule::EnableClassLoadCallbacks メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: 16516cceae9a10288f8660fa69d8e0c018953777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801086"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>ICorDebugModule::EnableClassLoadCallbacks メソッド

このモジュールに対して、" [UnloadClass](icordebugmanagedcallback-unloadclass-method.md) " コール[バック:: loadclass](icordebugmanagedcallback-loadclass-method.md)との各コールバックを呼び出すかどうかを制御します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `bClassLoadCallbacks`  
 からこの値をに設定する `true` と、共通言語ランタイム (CLR) が、 `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` 関連付けられたイベントが発生したときにメソッドとメソッドを呼び出すことができるようになります。  
  
 既定値は `false` 非動的モジュールの場合はです。 値は、動的モジュールの場合は常にであり `true` 、変更することはできません。  
  
## <a name="remarks"></a>解説  

 `ICorDebugManagedCallback::LoadClass`および `ICorDebugManagedCallback::UnloadClass` コールバックは動的モジュールに対して常に有効であり、無効にすることはできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
