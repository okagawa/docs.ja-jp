---
description: '詳細について: ICorDebugProcess5:: EnableNGENPolicy メソッド'
title: ICorDebugProcess5::EnableNGENPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: 0f3194893665bfe9fff802a293aaafed8254f2e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649924"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy メソッド

マネージデバッガーで実行中にアプリケーションがネイティブイメージを読み込む方法を決定する値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ePolicy`  
 からマネージデバッガーで実行中にアプリケーションがネイティブイメージを読み込む方法を決定する [Cordebugngenpolicy](cordebugngenpolicy-enumeration.md) 定数。  
  
## <a name="remarks"></a>解説  

 ポリシーが正常に設定されている場合、メソッドはを返し `S_OK` ます。 `ePolicy`が[Cordebugngenpolicy](cordebugngenpolicy-enumeration.md)によって定義された列挙値の範囲外にある場合、メソッドはを返し、 `E_INVALIDARG` メソッドの呼び出しは無効です。 ネイティブイメージジェネレーター (Ngen.exe) のポリシーを更新できない場合、メソッドはを返し `E_FAIL` ます。  
  
 メソッドは、 `ICorDebugProcess5::EnableNGenPolicy` プロセスの有効期間中、いつでも呼び出すことができます。 ポリシーは、ポリシーが設定された後に読み込まれるすべてのモジュールに対して有効です。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](icordebugprocess5-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
