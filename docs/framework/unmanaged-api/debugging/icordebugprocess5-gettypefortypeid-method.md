---
description: '詳細について: ICorDebugProcess5:: GetTypeForTypeID メソッド'
title: ICorDebugProcess5::GetTypeForTypeID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: a18543b0afc867dc3796264ac1d08a775c73ca59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746374"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a>ICorDebugProcess5::GetTypeForTypeID メソッド

型識別子をの型の値に変換します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `id`  
 から型識別子。  
  
 `ppType`  
 入出力テキストオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 場合によっては、型識別子を返すメソッドが null 値を返すことがあり `COR_TYPEID` ます。 この値が引数として渡された場合 `id` 、 `GetTypeForTypeID` メソッドは失敗し、を返し `E_FAIL` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](icordebugprocess5-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
