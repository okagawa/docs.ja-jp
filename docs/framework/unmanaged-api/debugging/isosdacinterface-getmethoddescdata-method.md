---
description: ': ISOSDacInterface:: GetMethodDescData メソッドの詳細について説明します。'
title: 'ISOSDacInterface:: GetMethodDescData メソッド'
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a1284aa4d810ed9d6db7ad3c1b471702b1dad54d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790426"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>ISOSDacInterface:: GetMethodDescData メソッド

指定された MethodDesc ポインターのデータを取得します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a>パラメーター

`methodDesc`\
からMethodDesc のアドレス。

`ip`\
からメソッドの IP アドレス。

`data`\
入出力内部 Api から返される MethodDesc に関連付けられたデータ。

`cRevertedRejitVersions`\
入出力戻された再 jit バージョンの数。

`rgRevertedRejitData`\
入出力内部 Api から返された、元に戻された rejit バージョンに関連付けられたデータ。

`pcNeededRevertedRejitData`\
入出力戻された ReJit バージョンに関連付けられたデータを格納するために必要なバイト数。

## <a name="remarks"></a>解説

指定されたメソッドはインターフェイスの一部で `ISOSDacInterface` あり、仮想メソッドテーブルの21スロットに対応します。 これらを使用できるようにするには、を [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) 64 ビット符号なし整数として定義する必要があります。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** 存在  
**ライブラリ:** 存在  
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [ISOSDacInterface インターフェイス](isosdacinterface-interface.md)
