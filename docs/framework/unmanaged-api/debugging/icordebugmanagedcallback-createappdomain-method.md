---
description: '詳細については、次の情報を参照してください: ICorDebugManagedCallback:: CreateAppDomain メソッド'
title: ICorDebugManagedCallback::CreateAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
ms.openlocfilehash: 5f4aa49ce90e8ec1343794db71ae3aa911c9e09f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791073"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a>ICorDebugManagedCallback::CreateAppDomain メソッド

アプリケーションドメインが作成されたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pProcess`  
 からアプリケーションドメインが作成されたプロセスを表す、のオブジェクトへのポインター。  
  
 `pAppDomain`  
 から作成されたアプリケーションドメインを表す、のオブジェクトへのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
