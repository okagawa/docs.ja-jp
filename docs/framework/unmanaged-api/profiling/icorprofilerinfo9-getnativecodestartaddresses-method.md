---
description: '詳細について: ICorProfilerInfo9:: GetNativeCodeStartAddresses メソッド'
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 1ca686cef4a45ebb9e05190fa790ed5300c0d816
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646492"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9:: GetNativeCodeStartAddresses メソッド

指定された functionId と rejitId は、現在存在する、このコードのすべての just-in-time バージョンのネイティブコードの開始アドレスを列挙します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a>パラメーター

- `functionId`

  \[in] ネイティブコードの開始アドレスを返す関数の ID。

- `reJitId`

  \[in) JIT 再コンパイルされた関数の id。

- `cCodeStartAddresses`

  \[in] 配列の最大サイズ `codeStartAddresses` 。

- `pcCodeStartAddresses`

  \[out] 使用可能なアドレスの数。

- `codeStartAddresses`

  \[out] の配列 `UINT_PTR` 。各は、指定された関数のネイティブ本体の開始アドレスです。

## <a name="remarks"></a>解説

階層化コンパイルが有効になっている場合、関数は複数のネイティブコード本体を持つことができます。

## <a name="requirements"></a>要件

**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo9 インターフェイス](icorprofilerinfo9-interface.md)
