---
description: '詳細について: ICorProfilerCallback:: ModuleUnloadStarted メソッド'
title: ICorProfilerCallback::ModuleUnloadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
ms.openlocfilehash: 3d10654e23481fe6f8956129a0aef7ed4206bba9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745230"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a>ICorProfilerCallback::ModuleUnloadStarted メソッド

モジュールがアンロードされていることをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a>パラメーター  

 `moduleId`  
 からアンロードされるモジュールの ID。  
  
## <a name="remarks"></a>解説  

 の値は、 `moduleId` メソッドから制御が戻った後の情報要求に対して有効ではありません `ModuleUnloadStarted` 。これは、このモジュールに関する情報を取得する最後の機会です。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
- [ModuleUnloadFinished メソッド](icorprofilercallback-moduleunloadfinished-method.md)
