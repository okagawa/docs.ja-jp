---
description: '詳細については、次のページを参照してください: GetArgumentIndex メソッド'
title: 'いい変数 Home:: GetArgumentIndex メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 827ef55d3e3509cbfbfc8213ef5b53fbe2e2220e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690042"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>いい変数 Home:: GetArgumentIndex メソッド

関数の引数のインデックスを取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>パラメーター

`pArgumentIndex`\
入出力引数インデックスへのポインター。

## <a name="return-value"></a>戻り値

メソッドは、次の値を返します。

|値|説明|
|-----------|-----------------|
|`S_OK`|メソッド呼び出しによって有効な引数インデックスが返されました。|
|`E_FAIL`|現在の [ページ](icordebugvariablehome-interface.md) は、ローカル変数を表します。|

## <a name="remarks"></a>解説

引数インデックスは、この引数のメタデータを取得するために使用できます。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>関連項目

- [ICorDebugVariableHome インターフェイス](icordebugvariablehome-interface.md)
