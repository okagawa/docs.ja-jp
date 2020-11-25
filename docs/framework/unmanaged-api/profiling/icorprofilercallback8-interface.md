---
title: ICorProfilerCallback8 インターフェイス
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 22a133d02bb69026190428905379323362943d40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732386"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 インターフェイス

[.NET Framework 4.7 以降のバージョンでサポートされています]  

 動的メソッドの JIT コンパイルが開始および終了したことをプロファイラーに通知するために、共通言語ランタイムによって使用されるコールバックメソッドを提供する [ICorProfilerCallback7](icorprofilercallback7-interface.md) のサブクラスです。
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted メソッド](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|動的メソッドの JIT コンパイルが開始されたことをプロファイラーに通知します。|  
|[DynamicMethodJITCompilationFinished メソッド](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|動的メソッドの JIT コンパイルが終了したことをプロファイラーに通知します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerCallback9 インターフェイス](icorprofilercallback9-interface.md)
