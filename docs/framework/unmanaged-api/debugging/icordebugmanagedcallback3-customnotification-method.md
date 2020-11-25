---
title: ICorDebugManagedCallback3::CustomNotification メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: f30c9b6746d0e1594994870a96e94eb8105e4c94
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700835"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a>ICorDebugManagedCallback3::CustomNotification メソッド

カスタムデバッガー通知が発生したことを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pThread`  
 から通知を発生させたスレッドへのポインター。  
  
 `pAppDomain`  
 から通知を発生させたスレッドを含むアプリケーションドメインへのポインター。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>解説  

 後続の [ICorDebugThread4:: Getcurrentcustomデバッガ通知](icordebugthread4-getcurrentcustomdebuggernotification-method.md) メソッドの呼び出しでは、メソッドに渡されたスレッドオブジェクトを取得し <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> ます。 スレッドオブジェクトの型は、 [ICorDebugProcess3:: SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) メソッドを呼び出すことによって既に有効になっている必要があります。 デバッガーは、スレッドオブジェクトのフィールドから型固有のパラメーターを読み取ることができ、応答をフィールドに格納できます。  
  
 [ICorDebug](icordebug-interface.md)インターフェイスでは、通知の種類やその内容にポリシーは適用されません。また、通知のセマンティクスは、厳密にはデバッガー、アプリケーション、および .NET Framework 間のコントラクトになります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback3 インターフェイス](icordebugmanagedcallback3-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
