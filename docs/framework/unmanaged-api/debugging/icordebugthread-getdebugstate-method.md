---
title: ICorDebugThread::GetDebugState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
ms.openlocfilehash: 746fef3629e6573d7dfe47d5a3fcf9ee9a1d4250
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728044"
---
# <a name="icordebugthreadgetdebugstate-method"></a>ICorDebugThread::GetDebugState メソッド

このスレッドオブジェクトの現在のデバッグ状態を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pState`  
 入出力このスレッドの現在のデバッグ状態を示す CorDebugThreadState 列挙値のビットごとの組み合わせへのポインター。  
  
## <a name="remarks"></a>注釈  

 プロセスが現在停止されている場合、は、 `pState` このスレッドの実際の現在の状態ではなく、プロセスが続行された場合に存在する可能性があるデバッグ状態を表します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
