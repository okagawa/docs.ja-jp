---
description: '詳細について: ICorProfilerInfo8:: GetFunctionFromIP3 メソッド'
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3ce0a0964e26254ab09e515826b6bceb657e07bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783834"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>ICorProfilerInfo8:: GetFunctionFromIP3 メソッド

マネージコード命令ポインターを FunctionID にマップします。 このメソッドは、動的メソッドと非動的メソッドの両方に対して機能します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a>パラメーター

- `ip`

  \[in) マネージコード内の命令ポインター。

- `pFunctionId`

  \[out] 関数 ID。

- `pReJitId`

  \[out] 関数の JIT 再コンパイルバージョンの id。

## <a name="remarks"></a>解説

このメソッドは、動的メソッドと非動的メソッドの両方に対して機能します。 これは [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)のスーパーセットであり、メタデータを持つ関数に対してのみ機能します。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo8 インターフェイス](icorprofilerinfo8-interface.md)
