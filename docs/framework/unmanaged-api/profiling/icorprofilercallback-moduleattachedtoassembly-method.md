---
description: '詳細について: ICorProfilerCallback:: ModuleAttachedToAssembly メソッド'
title: ICorProfilerCallback::ModuleAttachedToAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
ms.openlocfilehash: cc6a83188a8bdc4826232aa6ff6e416cbb8ae893
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705579"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly メソッド

モジュールが親アセンブリにアタッチされていることをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a>パラメーター  

 `moduleId`  
 からアタッチされているモジュールの ID。  
  
 `AssemblyId`  
 からモジュールがアタッチされている親アセンブリの ID。  
  
## <a name="remarks"></a>解説  

 モジュールは、インポートアドレステーブル (IAT)、の呼び出し、 `LoadLibrary` またはメタデータ参照を使用して読み込むことができます。 その結果、共通言語ランタイム (CLR) ローダーには、モジュールが存在するアセンブリを決定するための複数のコードパスがあります。 したがって、 [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) が呼び出された後、モジュールは、そのアセンブリを認識し、親アセンブリ ID を取得できない可能性があります。 この `ModuleAttachedToAssembly` メソッドは、モジュールが親アセンブリにアタッチされ、その親アセンブリ ID を取得できる場合に呼び出されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
