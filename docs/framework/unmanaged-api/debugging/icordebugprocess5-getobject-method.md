---
description: '詳細について: ICorDebugProcess5:: GetObject メソッド'
title: ICorDebugProcess5::GetObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: 4e295e1afc19cc5b9ca763b04b05097d48f0302c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746361"
---
# <a name="icordebugprocess5getobject-method"></a>ICorDebugProcess5::GetObject メソッド

オブジェクトのアドレスを "の値" オブジェクトに変換します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `addr`  
 からオブジェクトのアドレス。  
  
 `ppObject`  
 入出力"の値" オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 `addr`が有効なマネージオブジェクトを指していない場合、 `GetObject` メソッドはを返し `E_FAIL` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](icordebugprocess5-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
