---
title: ICorDebugController::Stop メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
ms.openlocfilehash: 11cc6e4108a2064a8a9fcefa760bf3c3411d63fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679859"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop メソッド

プロセスでマネージコードを実行しているすべてのスレッドで協調停止を実行します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwTimeoutIgnored`  
 使用されていません。  
  
## <a name="remarks"></a>注釈  

 `Stop` プロセスでマネージコードを実行しているすべてのスレッドで協調停止を実行します。 マネージ専用のデバッグセッションでは、アンマネージスレッドは引き続き実行できます (ただし、マネージコードを呼び出そうとするとブロックされます)。 相互運用機能デバッグセッションでは、アンマネージスレッドも停止します。 現在、この `dwTimeoutIgnored` 値は無視され、無限 (-1) として扱われます。 デッドロックが原因で協調停止が失敗した場合、すべてのスレッドが中断され、E_TIMEOUT が返されます。  
  
> [!NOTE]
> `Stop` は、デバッグ API の唯一の同期メソッドです。 `Stop`が S_OK を返した場合、プロセスは停止されます。 リスナーに停止を通知するためのコールバックが付与されていません。 デバッガーは、このプロセスを再開できるようにするために、を [実行](icordebugcontroller-continue-method.md) する必要があります。  
  
 デバッガーは停止カウンターを保持します。 カウンターが0になると、コントローラーが再開されます。 `Stop`またはディスパッチされた各コールバックの各呼び出しは、カウンターをインクリメントします。 を呼び出すたびに `ICorDebugController::Continue` カウンターがデクリメントされます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
