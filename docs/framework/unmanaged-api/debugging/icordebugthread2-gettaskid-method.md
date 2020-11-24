---
title: ICorDebugThread2::GetTaskID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: 9b17a179745af65bde05527bd0157f3ce06c12c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678663"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID メソッド

このスレッドで実行されているタスクの識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pTaskId`  
 入出力この ICorDebugThread2 オブジェクトによって表されるスレッド上で実行されているタスクの識別子へのポインター。  
  
## <a name="remarks"></a>注釈  

 スレッドが接続に関連付けられている場合にのみ、スレッドでタスクを実行できます。 `GetTaskID``pTaskId`スレッドが接続に関連付けられていない場合は、で0を返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
