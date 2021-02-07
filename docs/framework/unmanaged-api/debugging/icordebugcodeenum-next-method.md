---
description: 詳細については、次のメソッドを参照してください:、次のメソッド
title: ICorDebugCodeEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
ms.openlocfilehash: 51d46718891ce3df537c675175eacc4e33b92f79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764750"
---
# <a name="icordebugcodeenumnext-method"></a>ICorDebugCodeEnum::Next メソッド

現在の位置から開始して、指定した数の "コード" インスタンスを列挙から取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a>パラメーター

`celt`  
から `ICorDebugCode` 取得するインスタンスの数。

`values`  
入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugCode` ます。

`pceltFetched`  
入出力実際に返されたインスタンスの数へのポインター `ICorDebugCode` 。 が1の場合、この値は null `celt` になります。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
