---
description: '詳細について: ICorDebugProcess4::P rocessStateChanged メソッド'
title: ICorDebugProcess4::P rocessStateChanged メソッド
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 35a76b3c6dd9b37d3f06f23bc2ffea82f125a29e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746471"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::P rocessStateChanged メソッド

アウトプロセスデバッガーがデバッグ対象の実行を継続していることを ICorDebug パイプラインに通知します。

## <a name="syntax"></a>構文

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>パラメーター

 `eChange`\
からプロセスの実行状態の変更を記述する [CorDebugStateChange 列挙体](cordebugstatechange-enumeration.md) のメンバー。

## <a name="remarks"></a>解説

指定されたメソッドはインターフェイスの一部で `ICorDebugProcess4` あり、仮想メソッドテーブルの4番目のスロットに対応します。

## <a name="requirements"></a>要件

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

 **ヘッダー:** 存在

 **ライブラリ:** 存在

 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [ICorDebugProcess4 インターフェイス](icordebugprocess4-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
