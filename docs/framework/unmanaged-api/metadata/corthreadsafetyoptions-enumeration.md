---
description: 詳細については、「Corthreadsaf Etyoptions 列挙型」を参照してください。
title: CorThreadSafetyOptions 列挙型
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 7915bcf5e7b71fa84ea83642467c1600cd38712d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707320"
---
# <a name="corthreadsafetyoptions-enumeration"></a>CorThreadSafetyOptions 列挙型

スレッド セーフのオプションを選択するためのフラグを指定します。

## <a name="syntax"></a>構文

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a>メンバー

|メンバー|説明|
|------------|-----------------|
|`MDThreadSafetyDefault`|既定値です。 `MDThreadSafetyOff` と同じ。|
|`MDThreadSafetyOff`|リーダー/ライターロックを設定できないことを示します。|
|`MDThreadSafetyOn`|リーダー/ライターロックを設定できることを示します。|

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorHdr. h

**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
