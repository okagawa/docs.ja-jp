---
description: '詳細について: ICorProfilerCallback:: ModuleUnloadFinished メソッド'
title: ICorProfilerCallback::ModuleUnloadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: 32182beb879813a4e60f69494bd93799c0f66e1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745256"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a>ICorProfilerCallback::ModuleUnloadFinished メソッド

モジュールがアンロードを終了したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>パラメーター  

 `moduleId`  
 からアンロードされたモジュールの ID。  
  
 `hrStatus`  
 からモジュールが正常にアンロードされたかどうかを示す HRESULT。  
  
## <a name="remarks"></a>解説  

 `moduleId` [ICorProfilerCallback:: ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md)メソッドがを返すと、の値は情報要求に対して有効ではありません。  
  
 クラスのアンロードの一部は、コールバック後に続行される場合があり `ModuleUnloadFinished` ます。 のエラー HRESULT は `hrStatus` エラーを示します。 ただし、の成功 HRESULT は、 `hrStatus` モジュールのアンロードの最初の部分が成功したことを示します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
