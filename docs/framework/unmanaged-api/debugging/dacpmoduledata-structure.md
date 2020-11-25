---
title: DacpModuleData 構造体
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 5d27ba2de9ff6ed184b6ddf50a517d0dae7715f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723052"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData 構造体

モジュールのランタイム情報のトランスポートバッファーを定義します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a>メンバー

| メンバー    | 説明                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | モジュールオブジェクトのアドレス。                                           |
| `File`    | ポータブル実行可能 (PE) ファイルへのポインター。                       |
| `ilBase`  | 読み込まれたイメージのベースのアドレス。                                 |
| `payLoad` | ランタイムによって使用される追加のモジュール情報のペイロードバッファー。 |

## <a name="remarks"></a>注釈

この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。 これを使用するには、前に示したように構造体を定義します。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** 存在  
**ライブラリ:** 存在  
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [デバッグ構造体](debugging-structures.md)
