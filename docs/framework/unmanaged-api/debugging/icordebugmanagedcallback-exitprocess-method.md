---
description: '詳細については、次を参照してください: ExitProcess メソッド'
title: ICorDebugManagedCallback::ExitProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 3418931b8397edefcb801986275c35b28e00072d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790959"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>ICorDebugManagedCallback::ExitProcess メソッド

プロセスが終了したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pProcess`  
 からプロセスを表す、のオブジェクトへのポインター。  
  
## <a name="remarks"></a>解説  

 イベントから続行することはできません `ExitProcess` 。 このイベントは、プロセスの停止中に、他のイベントに非同期に発生する場合があります。 これは、プロセスが停止中に終了した場合に発生する可能性があります。通常は、何らかの外部強制が原因です。  
  
 共通言語ランタイム (CLR) がマネージコールバックのディスパッチを既に行っている場合、このイベントは、そのコールバックが返されるまで遅延されます。  
  
 `ExitProcess`イベントは、シャットダウン時に呼び出されることが保証されている唯一の終了/アンロードイベントです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
