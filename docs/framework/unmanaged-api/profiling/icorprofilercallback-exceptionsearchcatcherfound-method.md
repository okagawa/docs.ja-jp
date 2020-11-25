---
title: ICorProfilerCallback::ExceptionSearchCatcherFound メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: ef25d55defee2fdcfc7d744e481060eb7a7782ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699886"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a>ICorProfilerCallback::ExceptionSearchCatcherFound メソッド

例外処理の検索フェーズによってスローされた例外のハンドラーが見つかったことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>パラメーター

- `functionId`

  \[in] 例外ハンドラーを含む関数の ID。

## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
