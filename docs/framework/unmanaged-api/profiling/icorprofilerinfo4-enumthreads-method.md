---
description: '詳細について: ICorProfilerInfo4:: EnumThreads メソッド'
title: ICorProfilerInfo4::EnumThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: d597e68b8765e135d5bdb403dbdb161b7acbaa9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686935"
---
# <a name="icorprofilerinfo4enumthreads-method"></a>ICorProfilerInfo4::EnumThreads メソッド

プロファイリングされたプロセス内のすべてのマネージスレッドのコレクションを順番に反復処理するメソッドを提供する列挙子を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppEnum`  
 入出力 [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) インターフェイスへのポインター。  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerThreadEnum インターフェイス](icorprofilerthreadenum-interface.md)
- [ICorProfilerInfo4 インターフェイス](icorprofilerinfo4-interface.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [プロファイル](index.md)
