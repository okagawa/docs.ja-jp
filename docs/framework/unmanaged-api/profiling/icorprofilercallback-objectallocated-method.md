---
description: '詳細について: ICorProfilerCallback:: ObjectAllocated メソッド'
title: ICorProfilerCallback::ObjectAllocated メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: 58b58aeb4bb88d0df32cebc32440317a4d23632d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745165"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated メソッド

ヒープ内のメモリがオブジェクトに割り当てられたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>パラメーター  

 `objectId`  
 からメモリが割り当てられたオブジェクトの ID。  
  
 `classId`  
 からオブジェクトがインスタンスとして使用されているクラスの ID。  
  
## <a name="remarks"></a>解説  

 メソッドは、 `ObjectedAllocated` スタックまたはアンマネージメモリからの割り当てのために呼び出されません。 パラメーターは、 `classId` まだ読み込まれていないマネージコード内のクラスを参照できます。 プロファイラーは、コールバックの直後に、そのクラスのクラス読み込みコールバックを受け取り `ObjectAllocated` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
- [ClassLoadStarted メソッド](icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished メソッド](icorprofilercallback-classloadfinished-method.md)
