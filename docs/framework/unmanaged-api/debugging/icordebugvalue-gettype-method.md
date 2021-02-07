---
description: '詳細情報: ICorDebugValue:: GetType メソッド'
title: ICorDebugValue::GetType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 750e73634683a03e811d2756cc62c16b6dcea3de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690328"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType メソッド

この "ICorDebugValue" オブジェクトのプリミティブ型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pType`  
 入出力値の型を示す "CorElementType" 列挙値へのポインター。  
  
## <a name="remarks"></a>解説  

 オブジェクトが複雑な実行時の型である場合、その型はインターフェイスの適切なサブクラスを通じて検査される可能性があり `ICorDebugValue` ます。 たとえば、から継承する "" のような "という値は、 `ICorDebugValue` 複合型を表します。  
  
 `GetType`およびの各メソッドは、それぞれ値の型に関する情報[を](icordebugobjectvalue-getclass-method.md)返します。 これらはどちらも、ジェネリック対応 [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) メソッドに置き換えられています。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
