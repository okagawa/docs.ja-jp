---
description: '詳細について: ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 メソッド'
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
ms.openlocfilehash: c741054c50fb74afe79f10607e24424a07d2f8c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687026"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a>ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 メソッド

[FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)、および[FunctionTailcall3](functiontailcall3-function.md)の各関数で呼び出されるプロファイラー実装関数を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pFuncEnter3`  
 からコールバックとして使用される実装へのポインター `FunctionEnter3` 。  
  
 `pFuncLeave3`  
 からコールバックとして使用される実装へのポインター `FunctionLeave3` 。  
  
 `pFuncTailcall3`  
 からコールバックとして使用される実装へのポインター `FunctionTailcall3` 。  
  
## <a name="remarks"></a>解説  

 [FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)、および [FunctionTailcall3](functiontailcall3-function.md) フックは、スタックフレームと引数検査を提供しません。 この情報にアクセスするには、 `COR_PRF_ENABLE_FUNCTION_ARGS` 、 `COR_PRF_ENABLE_FUNCTION_RETVAL` 、および/または  `COR_PRF_ENABLE_FRAME_INFO` フラグを設定する必要があります。 プロファイラーは、 [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) メソッドを使用してイベントフラグを設定し、 [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) メソッドを使用してこの関数の実装を登録できます。  
  
 コールバックのセットは一度に1つしかアクティブにできません。また、最新バージョンが優先されます。 したがって、プロファイラーが [SetEnterLeaveFunctionHooks2 メソッド](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) とメソッドの両方を呼び出すと `SetEnterLeaveFunctionHooks3` 、 `SetEnterLeaveFunctionHooks3` が使用されます。  
  
 メソッドは、 `SetEnterLeaveFunctionHooks3` プロファイラーの [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) コールバックからのみ呼び出すことができます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [グローバル静的関数のプロファイル](profiling-global-static-functions.md)
- [ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [プロファイル](index.md)
