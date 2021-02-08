---
description: '詳細情報: DacpGetModuleAddress:: Request メソッド'
title: DacpGetModuleAddress::Request メソッド
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4cdec9cf6b9bd818ce1137fb5b2c691532fab94e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801502"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::Request メソッド

指定されたランタイム構造体を構造体に設定する要求を実行します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>パラメーター

`pDataModule`\
からシードデータモジュールへのポインター。

## <a name="remarks"></a>解説

この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。 これを使用する最も簡単な方法は、実装を模倣することです。

- 次のパラメーターを使用して、パラメーターのメソッドの呼び出しから取得した値を返し `Request` `IXCLRDataModule*` ます。 `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>要件

**プラットフォーム:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。\
**ヘッダー:** 存在
**ライブラリ:** 存在
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [DacpGetModuleAddress 構造体](dacpgetmoduleaddress-structure.md)
