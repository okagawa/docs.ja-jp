---
description: 詳細については、次を参照
title: ICorDebugManagedCallback::ExitThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: 4c9472d6377246833c7c30f072549da9c44f05d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790946"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a>ICorDebugManagedCallback::ExitThread メソッド

マネージコードを実行していたスレッドが終了したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pAppDomain`  
 からマネージスレッドを含むアプリケーションドメインを表す、コードの Appdomain オブジェクトへのポインター。  
  
 `thread`  
 からマネージスレッドを表す、コードスレッドオブジェクトへのポインター。  
  
## <a name="remarks"></a>解説  

 `ExitThread`コールバックが発生すると、スレッドはスレッド列挙に表示されなくなります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
