---
description: '詳細については、次を参照してください: DacpReJitData 構造体'
title: DacpReJitData 構造体
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 8e8d506856dbc6579ac6ea0eee2b2088a980a315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801437"
---
# <a name="dacprejitdata-structure"></a>DacpReJitData 構造体

プロファイラーによってインストルメント化された特定のメソッドに関する基本情報を定義します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a>メンバー

| メンバー           | 説明                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | メソッドの ReJit リビジョン番号。                                                          |
| `flags`          | 指定されたバージョンのメソッドの ReJit インストルメンテーションの現在の状態を示すフラグ。 |
| `NativeCodeAddr` | メソッドの rejitted 実装のベースアドレス。                                         |

## <a name="remarks"></a>解説

この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。 これを使用するには、前に示したように構造体を定義します。 `ms_struct`Microsoft コンパイラを使用していない場合は、パッキングを使用して構造体を定義する必要もあります。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** 存在  
**ライブラリ:** 存在  
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [デバッグ構造体](debugging-structures.md)
