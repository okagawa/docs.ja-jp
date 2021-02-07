---
description: '詳細については、次のページを参照してください: いいね。'
title: ICorDebugController::Continue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
ms.openlocfilehash: e5858a8c287e8dd5a493a85c9f427ad8acd9ecc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710804"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue メソッド

[Stop メソッド](icordebugcontroller-stop-method.md)の呼び出し後に、マネージスレッドの実行を再開します。

## <a name="syntax"></a>構文

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a>パラメーター

`fIsOutOfBand`  
から `true` 帯域外イベントから続行する場合はに設定し、それ以外の場合はに設定 `false` します。

## <a name="remarks"></a>解説

`Continue` メソッドの呼び出し後にプロセスを続行し `ICorDebugController::Stop` ます。

混合モードのデバッグを実行する場合は、 `Continue` 帯域外のイベントから継続している場合を除き、Win32 イベントスレッドでを呼び出さないでください。

*帯域内イベント* は、マネージイベント、またはデバッガーがプロセスのマネージ状態との対話をサポートする通常のアンマネージイベントのいずれかです。 この場合、デバッガーは、パラメーターがに設定された状態で [ICorDebugUnmanagedCallback::D Eのイベント](icordebugunmanagedcallback-debugevent-method.md) コールバックを受け取り `fOutOfBand` `false` ます。

*アウトオブバンドイベント* は、イベントによってプロセスが停止されている間に、プロセスのマネージ状態との相互作用が不可能なアンマネージイベントです。 この場合、デバッガーは `ICorDebugUnmanagedCallback::DebugEvent` `fOutOfBand` パラメーターをに設定してコールバックを受け取り `true` ます。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
