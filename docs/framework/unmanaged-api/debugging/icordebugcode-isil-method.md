---
description: '詳細情報: 「コード:: IsIL メソッド」を参照してください。'
title: ICorDebugCode::IsIL メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
ms.openlocfilehash: db41f9ebaa6a6403b21e10d1daa0e8b167c7cb96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711127"
---
# <a name="icordebugcodeisil-method"></a>ICorDebugCode::IsIL メソッド

この "コードが、Microsoft 中間言語 (MSIL) でコンパイルされたコードを表しているかどうかを示す値を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a>パラメーター

`pbIL`  
[出力] `true` このが `ICorDebugCode` MSIL でコンパイルされたコードを表す場合は。それ以外の場合は `false` 。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
