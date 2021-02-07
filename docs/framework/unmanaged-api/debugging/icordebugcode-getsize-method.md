---
description: '詳細情報: 「コード:: GetSize メソッド」を参照してください。'
title: ICorDebugCode::GetSize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
ms.openlocfilehash: 5a244d649cdcf027aea22ab36ff5d39a77a05e1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711181"
---
# <a name="icordebugcodegetsize-method"></a>ICorDebugCode::GetSize メソッド

この "コード" によって表されるバイナリコードのサイズ (バイト単位) を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a>パラメーター

`pcBytes`  
入出力このオブジェクトが表すバイナリコードのサイズ (バイト単位) へのポインター `ICorDebugCode` 。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
