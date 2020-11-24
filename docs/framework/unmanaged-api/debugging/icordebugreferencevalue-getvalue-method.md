---
title: ICorDebugReferenceValue::GetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type:
- apiref
ms.openlocfilehash: cbdba623b02ccc85c6d4784a9539adf14fd256e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691202"
---
# <a name="icordebugreferencevaluegetvalue-method"></a>ICorDebugReferenceValue::GetValue メソッド

参照先のオブジェクトの現在のメモリアドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pValue`  
 入出力このは、 `CORDB_ADDRESS` この参照値オブジェクトが指すオブジェクトのアドレスを指定する値へのポインターです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
