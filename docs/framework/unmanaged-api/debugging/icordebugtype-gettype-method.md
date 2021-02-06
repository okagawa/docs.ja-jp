---
description: '詳細については、次を参照してください: の型:: GetType type:: GetType メソッド'
title: ICorDebugType::GetType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: 922791e51855badfb1fd548e08953a2f660f971a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658218"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType メソッド

<xref:System.Type>このコンポーネント型によって表される共通言語ランタイム (CLR) のネイティブ型を記述する CorElementType 値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ty`  
 入出力 `CorElementType` このが表す CLR を示す列挙体の値へのポインター <xref:System.Type> `ICorDebugType` 。  
  
## <a name="remarks"></a>解説  

 の値 `ty` が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の場合は、インスタンス type [:: getclass](icordebugtype-getclass-method.md) メソッドを呼び出してジェネリック型の型を取得することができます。それ以外の場合は、を呼び出さないで `ICorDebugType::GetClass` ください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
