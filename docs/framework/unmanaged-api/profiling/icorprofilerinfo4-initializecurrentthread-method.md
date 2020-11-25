---
title: ICorProfilerInfo4::InitializeCurrentThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: 51f16523c00cc3dd95b786f1586ccfd75ce8d5f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733829"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread メソッド

デッドロックを回避できるように、同じスレッドで、後続のプロファイラー API 呼び出しの前に現在のスレッドを初期化します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>解説  

 中断された `InitializeCurrentThread` スレッドがある間は、PROFILER API を呼び出すスレッドでを呼び出すことをお勧めします。 このメソッドは、通常、 [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) メソッドを呼び出して、ターゲットスレッドが中断されている間にスタックウォークを実行する独自のスレッドを作成する、サンプリングプロファイラーによって使用されます。 プロファイラーでは、最初にサンプリングスレッドを作成するときにを呼び出すことによって `InitializeCurrentThread` 、 `DoStackSnapshot` 他のスレッドが中断されていないときに、CLR がの最初の呼び出し時に実行する、スレッドごとの遅延初期化を安全に行うことができます。  
  
> [!NOTE]
> `InitializeCurrentThread` は、ロックを受け取るタスクを完了するために事前に初期化し、デッドロックが発生する可能性があります。 `InitializeCurrentThread`中断されたスレッドが存在しない場合にのみ、を呼び出します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo4 インターフェイス](icorprofilerinfo4-interface.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [プロファイル](index.md)
