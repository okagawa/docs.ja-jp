---
description: '詳細について: ICorProfilerInfo8:: GetDynamicFunctionInfo メソッド'
title: 'ICorProfilerInfo8:: GetDynamicFunctionInfo'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 48c8dbe20ccafb3fb23e9e289f728d5e3370613a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646583"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: GetDynamicFunctionInfo メソッド

動的メソッドに関する情報を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a>パラメーター

- `functionId`

  \[in] 情報を取得する関数の ID。

- `moduleId`

  \[では、関数の親クラスが定義されているモジュールへのポインター。

- `ppvSig`

  \[out] 関数のシグネチャへのポインター。

- `pbSig`

  \[out] 関数シグネチャのバイト数へのポインター。

- `cchName`

  \[in] 配列の最大サイズ `wszName` 。

- `pcchName`

  \[out] 配列内の文字数 `wszName` 。

- `wszName`

  \[out] `WCHAR` 関数の名前 (存在する場合) の配列。

## <a name="remarks"></a>解説

IL スタブや LCG などの特定のメソッドには、 [IMetaDataImport](../metadata/imetadataimport-interface.md) Api と [IMetaDataImport2](../metadata/imetadataimport2-interface.md) api を使用して取得できるメタデータが関連付けられていません。 このようなメソッドは、命令ポインターを通じて、または [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)をリッスンすることによって、プロファイラーによって検出されます。

この API を使用して、表示名などの動的メソッドに関する情報を取得できます (使用可能な場合)。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo8 インターフェイス](icorprofilerinfo8-interface.md)
