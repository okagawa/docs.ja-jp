---
title: 'IXCLRDataProcess:: GetRuntimeNameByAddress メソッド'
ms.date: 4/27/2020
api.name:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: tommcdon
ms.author: tommcdon
ms.openlocfilehash: 6648bdafe6e5cdd402bcfa02a148c57f0f1e209e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96297169"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a>IXCLRDataProcess:: GetRuntimeNameByAddress メソッド

指定されたアドレスの名前を取得します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT GetRuntimeNameByAddress(
    [in] CLRDATA_ADDRESS address,
    [in] ULONG32 flags,
    [in] ULONG32 bufLen,
    [out] ULONG32 *nameLen,
    [out, size_is(bufLen)] WCHAR nameBuf[],
    [out] CLRDATA_ADDRESS* displacement
);
```

## <a name="parameters"></a>パラメーター

`address`\
から `CLRDATA_ADDRESS` コードアドレスを表す値。

`flags`\
からを ' 0 ' に設定します。

`bufLen`\
からバッファーの長さ。

`namLen`\
入出力返された文字数へのポインター。

`namBuf`\
[out, size_is ( `bufLen` )] ランタイム名を格納する長さの入力バッファー `bufLen` 。

`displacement`\
入出力 `CLRDATA_ADDRESS` 返されたシンボルのコードオフセットへのポインター。

## <a name="remarks"></a>解説

指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの16番目のスロットに対応します。

> [!NOTE]
> バッファーが名前に十分な大きさではない場合、このメソッドはを返し、 `S_FALSE` `nameLen` に必要なバッファー長を設定します。

## <a name="requirements"></a>要件

**プラットフォーム:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。\
**ヘッダー:** 存在
**ライブラリ:** 存在
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [IXCLRDataProcess インターフェイス](ixclrdataprocess-interface.md)
