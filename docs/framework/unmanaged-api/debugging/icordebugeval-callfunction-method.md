---
description: '詳細については、次を参照してください: いいね:: CallFunction メソッド'
title: ICorDebugEval::CallFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: c0978ab3bdffc83e3eb5e3a6553e7f374ab6d5da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694189"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction メソッド

指定された関数の呼び出しを設定します。

このメソッドは .NET Framework バージョン2.0 では廃止されています。 代わりに [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) を使用してください。

## <a name="syntax"></a>構文

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a>パラメーター

`pFunction`\
から呼び出される関数を指定する、のオブジェクトへのポインター。

`nArgs`\
から関数の引数の数。

`ppArgs`\
からポインターの配列。各ポインターは、関数に渡される引数を指定する ICorDebugValue オブジェクトを指します。

## <a name="remarks"></a>解説

関数が virtual の場合、 `CallFunction` は仮想ディスパッチを実行します。 関数が別のアプリケーションドメインにある場合は、すべての引数がそのアプリケーションドメインにも存在する限り、遷移が発生します。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:** 1.1、1.0

## <a name="see-also"></a>関連項目

- [CallParameterizedFunction メソッド](icordebugeval2-callparameterizedfunction-method.md)
