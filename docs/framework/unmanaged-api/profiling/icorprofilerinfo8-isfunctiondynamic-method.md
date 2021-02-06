---
description: '詳細について: ICorProfilerInfo8:: IsFunctionDynamic メソッド'
title: 'ICorProfilerInfo8:: IsFunctionDynamic'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8ab942e6919f8029ef0d1c20336917622a1d22ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646531"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>ICorProfilerInfo8:: IsFunctionDynamic メソッド

関数にメタデータが関連付けられていないかどうかを判断します。

## <a name="syntax"></a>構文

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a>パラメーター

- `functionId`

  \[in] `FunctionID` 対象の関数を識別する。

- `isDynamic`

  \[out] `BOOL` 関数にメタデータが含まれていないかどうかを示す値を格納するへのポインター。

## <a name="remarks"></a>解説

関数は、メタデータがない場合は動的と見なされます。 IL スタブや LCG メソッドなどの特定のメソッドには、IMetaDataImport Api を使用して取得できるメタデータが関連付けられていません。 これらのメソッドは、命令ポインターを通じて、または [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)をリッスンすることによって、プロファイラーによって検出されます。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo8 インターフェイス](icorprofilerinfo8-interface.md)
