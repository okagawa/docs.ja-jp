---
title: ICorDebugModule::IsDynamic メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 98c01993a85ed07d961902d8a098a96df4702c76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709831"
---
# <a name="icordebugmoduleisdynamic-method"></a>ICorDebugModule::IsDynamic メソッド

このモジュールが動的かどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pDynamic`  
 [出力] `true` このモジュールが動的である場合は。それ以外の場合は `false` 。  
  
## <a name="remarks"></a>注釈  

 動的モジュールは、モジュールが読み込まれた後でも、新しいクラスを追加したり、既存のクラスを削除したりできます。 は、クラスが追加または削除されたときに、 [UnloadClass](icordebugmanagedcallback-unloadclass-method.md) [Callback:: loadclass](icordebugmanagedcallback-loadclass-method.md)コールバックとによって、デバッガーに通知します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
