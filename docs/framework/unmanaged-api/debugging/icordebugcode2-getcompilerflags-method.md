---
description: '詳細について: ICorDebugCode2:: GetCompilerFlags メソッド'
title: ICorDebugCode2::GetCompilerFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
ms.openlocfilehash: 820b6d2392b2b91bbfc8a85b165c4d73a2546859
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711119"
---
# <a name="icordebugcode2getcompilerflags-method"></a>ICorDebugCode2::GetCompilerFlags メソッド

このコード オブジェクトが Just-In-Time (JIT) コンパイルされたとき、またはネイティブ イメージ ジェネレーター (Ngen.exe) を使用して生成されたときの条件を指定するフラグを取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a>パラメーター

`pdwFlags`  
入出力JIT コンパイラまたはネイティブイメージジェネレーターの動作を指定する [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列挙値へのポインター。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
