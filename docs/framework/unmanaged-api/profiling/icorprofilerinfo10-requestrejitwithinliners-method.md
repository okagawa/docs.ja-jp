---
description: '詳細について: ICorProfilerInfo10:: RequestReJITWithInliners メソッド'
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: da3434926b36408adfdee2171d56f23ba764f0eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753264"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10:: RequestReJITWithInliners メソッド

要求されたメソッドのほか、要求されたメソッドの inliners を再適用します。

## <a name="syntax"></a>構文

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a>パラメーター

- `dwRejitFlags`

  \[in) [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)のビットマスク。

- `cFunctions`

  \[in] 再コンパイルする関数の数。

- `moduleIds`

  \[in] は、再 `moduleId` `module` コンパイルする関数を識別する (、) ペアの部分を指定し `methodDef` ます。

- `methodIds`

  \[in] は、再 `methodId` `module` コンパイルする関数を識別する (、) ペアの部分を指定し `methodDef` ます。

## <a name="remarks"></a>解説

[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) では、インラインメソッドの追跡は行われません。 プロファイラーは、インライン化された `RequestReJIT` メソッドのすべてのインスタンスが ReJITted であることを確認するために、インライン展開をブロックするか、インライン展開を追跡し、すべての inliners に対してを呼び出す必要がありました これにより、再インライン化を監視するためのプロファイラーが存在しないため、ReJIT on attach に問題が生じます。 このメソッドを呼び出すことにより、inliners の完全なセットも ReJITted になることを保証できます。

## <a name="requirements"></a>要件

**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 インターフェイス](icorprofilerinfo10-interface.md)
