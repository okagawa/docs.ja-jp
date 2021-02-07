---
description: '詳細について: ICorDebugValue2:: GetExactType メソッド'
title: ICorDebugValue2::GetExactType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: d0ef08b119106ced89ec2094b5bf67d0c874b6bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690306"
---
# <a name="icordebugvalue2getexacttype-method"></a>ICorDebugValue2::GetExactType メソッド

この値のを表す "の型" オブジェクトへのインターフェイスポインターを取得し <xref:System.Type> ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppType`  
 入出力 `ICorDebugType` <xref:System.Type> この "ICorDebugValue2" オブジェクトによって表される値のを表すオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 ジェネリック対応のメソッドは、 `GetExactType` という2つ[のメソッド](icordebugvalue-gettype-method.md)(それぞれが値の型についての情報を返す) を置き換え[ます。](icordebugobjectvalue-getclass-method.md)  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
