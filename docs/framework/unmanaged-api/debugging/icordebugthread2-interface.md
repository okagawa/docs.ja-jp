---
title: ICorDebugThread2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: a7a8d96548704f223f05826af79a4e227bdfab06
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379832"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 インターフェイス
は、"、" スレッドインターフェイスの論理的な拡張として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetActiveFunctions メソッド](icordebugthread2-getactivefunctions-method.md)|スレッドのフレーム内のアクティブな関数に関するデータを格納している COR_ACTIVE_FUNCTION インスタンスの配列を取得します。|  
|[GetConnectionID メソッド](icordebugthread2-getconnectionid-method.md)|このの接続識別子を取得し `ICorDebugThread2` ます。|  
|[GetTaskID メソッド](icordebugthread2-gettaskid-method.md)|こののタスク識別子を取得し `ICorDebugThread2` ます。|  
|[GetVolatileOSThreadID メソッド](icordebugthread2-getvolatileosthreadid-method.md)|こののオペレーティングシステムスレッド識別子を取得し `ICorDebugThread2` ます。|  
|[InterceptCurrentException メソッド](icordebugthread2-interceptcurrentexception-method.md)|デバッガーがスレッドの現在の例外をインターセプトできるようにします。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
