---
title: ICorDebugType::GetClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 1cb9729f175a2e82e88386b0694467c6fe05636a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684461"
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass メソッド

インスタンスジェネリック型を表す、のクラスへのインターフェイスポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppClass`  
 入出力 `ICorDebugClass` インスタンスジェネリック型を表すインターフェイスのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 `GetClass` は、特定の条件下でのみ呼び出すことができます。 を [呼び出す前に](icordebugtype-gettype-method.md) 、を呼び出して `GetClass` ください。 `ICorDebugType::GetType`が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の CorElementType 値を返す場合は、を呼び出して、 `GetClass` ジェネリック型のインスタンス型を取得できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
