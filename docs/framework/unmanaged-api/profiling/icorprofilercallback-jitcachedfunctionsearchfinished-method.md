---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: fe07270989df897c3dbf689305784f9f0af65742
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684045"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished メソッド

以前にネイティブイメージジェネレーター (NGen.exe) を使用してコンパイルされた関数の検索が終了したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>パラメーター

- `functionId`

  \[in] 検索が実行された関数の ID。

- `result`

  \[in] 検索の結果を示す [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) 列挙体の値。

## <a name="remarks"></a>注釈  

 .NET Framework バージョン2.0 では、通常の NGen イメージのすべての関数に対して [ICorProfilerCallback:: JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) と `JITCachedFunctionSearchFinished` コールバックは行われません。 プロファイラー用に最適化された NGen イメージのみが、イメージ内のすべての関数のコールバックを生成します。 ただし、オーバーヘッドが増加するため、プロファイラーは、これらのコールバックを使用して just-in-time (JIT) コンパイルを強制的に実行する場合にのみ、プロファイラーで最適化された NGen イメージを要求する必要があります。 それ以外の場合、プロファイラーは関数情報を収集するためにレイジー戦略を使用する必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
