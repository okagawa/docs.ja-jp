---
description: '詳細情報: CLRDATA_IL_ADDRESS_MAP 構造'
title: CLRDATA_IL_ADDRESS_MAP 構造体
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 02ee14154de0c1609e58cf6a2ad1ca62710567f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801853"
---
# <a name="clrdata_il_address_map-structure"></a>CLRDATA_IL_ADDRESS_MAP 構造体

アドレスマッピングの IL を定義します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a>メンバー

| メンバー         | 説明                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | 含まれているアドレス範囲の IL オフセット              |
| `startAddress` | 範囲の開始アドレス。                        |
| `endAddress`   | 範囲の終了アドレス。                          |
| `type`         | データの型。 この値は現在使用されていません |

## <a name="remarks"></a>解説

この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。 これを使用するには、上で指定したように構造体を定義し `CLRDATA_ADDRESS` ます。は、64ビットの符号なし整数です。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** 存在  
**ライブラリ:** なし **.NET Framework バージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [CLRDataSourceType 列挙型](clrdatasourcetype-enumeration.md)
- [デバッグ](index.md)
- [デバッグ構造体](debugging-structures.md)
