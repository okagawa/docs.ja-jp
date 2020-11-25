---
title: ICorProfilerCallback::RuntimeSuspendStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: b778088f53a3c49def95d715f5fefcb26af81489
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731983"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a>ICorProfilerCallback::RuntimeSuspendStarted メソッド

ランタイムがすべてのランタイムスレッドを中断しようとしていることをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a>パラメーター  

 `suspendReason`  
 から中断の理由を示す [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) 列挙体の値。  
  
## <a name="remarks"></a>注釈  

 アンマネージコード内のすべてのランタイムスレッドは、ランタイムを再入力しようとするまで実行を継続できます。 その時点で、ランタイムが再開されるまで中断されます。 これは、ランタイムに入る新しいスレッドにも当てはまります。 ランタイム内のすべてのスレッドは、割り込み可能なコードに既に存在する場合は直ちに中断されます。または、割り込み可能なコードになると中断するように求められます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
- [RuntimeSuspendAborted メソッド](icorprofilercallback-runtimesuspendaborted-method.md)
- [RuntimeSuspendFinished メソッド](icorprofilercallback-runtimesuspendfinished-method.md)
