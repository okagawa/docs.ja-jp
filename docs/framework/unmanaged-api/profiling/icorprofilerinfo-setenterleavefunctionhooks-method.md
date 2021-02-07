---
description: '詳細について: ICorProfilerInfo:: SetEnterLeaveFunctionHooks メソッド'
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: 45c161a76f3ae568da6a83a2c45acb214a327ff1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687208"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks メソッド

マネージ関数の "enter"、"leave"、および "tailcall" フックで呼び出されるプロファイラー実装関数を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pFuncEnter`  
 から [Functionenter](functionenter-function.md) コールバックとして使用される実装へのポインター。  
  
 `pFuncLeave`  
 から [Functionleave](functionleave-function.md) コールバックとして使用される実装へのポインター。  
  
 `pFuncTailcall`  
 から [FunctionTailcall](functiontailcall-function.md) コールバックとして使用される実装へのポインター。  
  
## <a name="remarks"></a>解説  

 .NET Framework バージョン1.0 では、対応するコールバックを無効にするために、各関数ポインターを null にすることができます。  
  
 一度にアクティブにできるコールバックのセットは1つだけです。 したがって、プロファイラーが `SetEnterLeaveFunctionHooks` と [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)の両方を呼び出すと、が `SetEnterLeaveFunctionHooks2` 優先されます。  
  
 `SetEnterLeaveFunctionHooks`メソッドを呼び出すことができるのは、プロファイラーの[ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)コールバックからだけです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
