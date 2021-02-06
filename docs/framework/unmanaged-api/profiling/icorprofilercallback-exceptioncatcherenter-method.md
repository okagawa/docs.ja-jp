---
description: '詳細について: ICorProfilerCallback:: ExceptionCatcherEnter メソッド'
title: ICorProfilerCallback::ExceptionCatcherEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 3a813936a7d1f3a5041e192c85d02b37976e3388
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657633"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter メソッド

適切なブロックに制御が渡されていることをプロファイラーに通知し `catch` ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>パラメーター

- `functionId`

  \[in] ブロックを含む関数の識別子 `catch` 。
  
- `objectId`

  \[in] 処理されている例外の識別子。

## <a name="remarks"></a>解説  

 メソッドは、 `ExceptionCatcherEnter` catch ポイントが just-in-time (JIT) コンパイラを使用してコンパイルされたコード内にある場合にのみ呼び出されます。 アンマネージコードまたはランタイムの内部コードでキャッチされた例外は、この通知を呼び出しません。 `objectId`通知後にガベージコレクションがオブジェクトを移動した可能性があるため、値は再度渡され `ExceptionThrown` ます。  
  
 プロファイラーは、このメソッドの実装でブロックしないでください。スタックがガベージコレクションを許可する状態にならないため、プリエンプティブガベージコレクションを有効にすることはできません。 プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。  
  
 プロファイラーによるこのメソッドの実装では、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
- [ExceptionCatcherLeave メソッド](icorprofilercallback-exceptioncatcherleave-method.md)
