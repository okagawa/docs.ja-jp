---
title: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type:
- apiref
ms.openlocfilehash: b0d94f5004da85caf0460e8f1d1b2d964944b045
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727069"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo メソッド

`catch` / `finally` / `filter` 実行される、または実行されたばかりの例外句 () のネイティブアドレスとフレーム情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pinfo`  
 入出力現在の exception 句のインスタンスとそれに関連付けられているフレームを記述する [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) 構造体へのポインター。  
  
## <a name="remarks"></a>注釈  

 例外通知が受信されると、を使用して、実行しようとし `GetNotifiedExceptionClauseInfo` ている例外句 () のネイティブアドレスとフレーム情報を取得できます `catch` / `finally` / `filter` ([ICorProfilerCallback:: ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)、 [ICorProfilerCallback:: ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)、または[ICorProfilerCallback:: exceptionsearchfilterenter](icorprofilercallback-exceptionsearchfilterenter-method.md)コールバックがプロファイラーによって受信されたか、実行された直後 ([ICorProfilerCallback:: ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)、 [ICorProfilerCallback:: ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)、または[ICorProfilerCallback:: exceptionsearchfilterenter](icorprofilercallback-exceptionsearchfilterleave-method.md)コールバックがプロファイラーによって受信されました)。  
  
 この呼び出しは、一致する Leave コールバックが受信されるか、または現在の句で入れ子になった例外がスローされるまで、任意の時点でいつでも実行できます。その場合、その句には Leave 通知がありません。 スローされた例外が例外句をエスケープすることはできないの `filter` で、その場合は常に Leave 通知が存在することに注意してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](icorprofilerinfo2-interface.md)
