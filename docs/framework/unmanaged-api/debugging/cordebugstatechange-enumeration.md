---
description: '詳細については、次を参照してください: CorDebugStateChange 列挙型'
title: CorDebugStateChange 列挙体
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
ms.openlocfilehash: 1900baa77432daa10d0f1a32dd9cb25198b86ed1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661819"
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange 列挙体

プロセスへの変更に基づいて破棄が必要となった、キャッシュされたデータの量を示します。

## <a name="syntax"></a>構文

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>メンバー

| メンバー            | 説明                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | プロセスはフォワード実行によって新しいメモリ状態に達しています。            |
| `FLUSH_ALL`       | プロセスのメモリは、以前とは異なる状態になっている場合があります。 |

## <a name="remarks"></a>解説

 `CorDebugStateChange`デバッガーが `ProcessStateChanged` [ICorDebugProcess4::P Rocessstatechanged](icordebugprocess4-processstatechanged-method.md)または[ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)を使用してメソッドを呼び出すと、列挙体のメンバーが引数として提供されます。

## <a name="requirements"></a>要件

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

 **ヘッダー:** CorDebug.idl、CorDebug.h

 **ライブラリ:** CorGuids.lib

 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
- [デバッグ](index.md)
