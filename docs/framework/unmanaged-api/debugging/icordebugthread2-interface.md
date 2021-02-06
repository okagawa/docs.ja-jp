---
description: 詳細については、「ICorDebugThread2 インターフェイス」を参照してください。
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
ms.openlocfilehash: 81f687f6daff9ffa7298ec6d818a214b8934bcc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658504"
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
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
