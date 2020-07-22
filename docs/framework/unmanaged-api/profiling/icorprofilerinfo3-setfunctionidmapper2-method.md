---
title: ICorProfilerInfo3::SetFunctionIDMapper2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 723cb277a7df592e0494505018f7422e4e40f5f6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496153"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a>ICorProfilerInfo3::SetFunctionIDMapper2 メソッド
`FunctionID` 値を代替値に対応付けるために呼び出すプロファイラー実装関数を指定します。代替値は、プロファイラーの関数の開始フックと終了フックに渡されます。 このメソッドは、追加のデータパラメーターを使用して[ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)メソッドを拡張します。これは、プロファイラーがランタイムを明確に区別するために使用する可能性があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pFunc`  
 から[FunctionIDMapper2](functionidmapper2-function.md) `FunctionID` 値を代替値にマップするために呼び出される FunctionIDMapper2 実装へのポインター。  
  
 `clientData`  
 から現在のランタイムによって行われたすべての[FunctionIDMapper2](functionidmapper2-function.md)関数呼び出しに渡されるポインター。 プロファイラーはこの情報を使用して、ランタイム間を明確に区別できます。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>解説  
 FunctionID 値の代替手段は、 [FunctionLeave3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)または[FunctionTailcall3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)メソッドによって指定されたプロファイラーの関数の開始/終了フック ([FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)、 [FunctionTailcall3](functiontailcall3-function.md)、 [FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [SetEnterLeaveFunctionHooks3](functionleave3withinfo-function.md)、および[SetEnterLeaveFunctionHooks3WithInfo](functiontailcall3withinfo-function.md)) に渡されます。  
  
 `FunctionIDMapper2`メソッドを設定できるのは1回だけです。 [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)コールバックで設定することをお勧めします。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3 インターフェイス](icorprofilerinfo3-interface.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [プロファイル](index.md)
