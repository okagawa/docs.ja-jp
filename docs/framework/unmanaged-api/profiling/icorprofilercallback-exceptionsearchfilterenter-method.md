---
description: '詳細について: ICorProfilerCallback:: ExceptionSearchFilterEnter メソッド'
title: ICorProfilerCallback::ExceptionSearchFilterEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
ms.openlocfilehash: ca0eb80f57d7c00d0abfab1bb602650c951a30e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745365"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a>ICorProfilerCallback::ExceptionSearchFilterEnter メソッド

例外処理の検索フェーズがユーザー定義の例外フィルターの実行を開始したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>パラメーター

- `functionId`

  \[in] フィルターを含む関数の ID。

## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
- [ExceptionSearchFilterLeave メソッド](icorprofilercallback-exceptionsearchfilterleave-method.md)
