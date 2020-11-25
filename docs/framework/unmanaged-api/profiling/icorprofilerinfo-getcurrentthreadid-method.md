---
title: ICorProfilerInfo::GetCurrentThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
ms.openlocfilehash: 18298c4c726d7d850e67afbf82ca77b7511d8917
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722592"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a>ICorProfilerInfo::GetCurrentThreadID メソッド

マネージスレッドの場合、現在のスレッドの ID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pThreadId`  
 入出力返されたマネージスレッドの ID へのポインター。  
  
## <a name="remarks"></a>注釈  

 現在のスレッドが内部ランタイムスレッドまたはその他のアンマネージスレッドである場合、は `GetCurrentThreadID` CORPROF_E_NOT_MANAGED_THREAD を HRESULT として返し、パラメーターの戻り値は null になり `pThreadId` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
