---
description: '詳細について: ICorDebugCode2:: GetCodeChunks メソッド'
title: ICorDebugCode2::GetCodeChunks メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
ms.openlocfilehash: 371d077466ff2390293d9d4e320d4c95a992fe54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764969"
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks メソッド

このコード オブジェクトを構成しているコード チャンクを取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a>パラメーター

`cbufSize`  
から配列のサイズ `chunks` 。

`pcnumChunks`  
入出力配列で返されたチャンクの数 `chunks` 。

`chunks`  
入出力"CodeChunkInfo" 構造体の配列。それぞれが1つのコードチャンクを表します。 の値 `cbufSize` が0の場合、このパラメーターには null を指定できます。

## <a name="remarks"></a>解説

コードチャンクは重複しません。コードチャンクは、「 [コード:: GetCode](icordebugcode-getcode-method.md)」によって連結された順序に従います。 .NET Framework バージョン2.0 の Microsoft 中間言語 (MSIL) コードオブジェクトは、1つのコードチャンクを構成します。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
