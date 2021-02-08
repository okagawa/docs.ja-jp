---
description: '詳細については、次を参照してください: CreateThread メソッド'
title: ICorDebugManagedCallback::CreateThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 20d5ce9da34e7082502252eeece2ab34b1f2e902
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791033"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a>ICorDebugManagedCallback::CreateThread メソッド

スレッドがマネージコードの実行を開始したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pAppDomain`  
 からスレッドを含むアプリケーションドメインを表す、のオブジェクトへのポインター。  
  
 `thread`  
 からスレッドを表す、スレッドオブジェクトへのポインター。  
  
## <a name="remarks"></a>解説  

 スレッドは、実行される最初のマネージコード命令に配置されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
