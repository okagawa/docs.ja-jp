---
description: '詳細については、次を参照してください: を参照してください。値:: SetValue メソッド'
title: ICorDebugReferenceValue::SetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
ms.openlocfilehash: 44909962d2716ddb606d98a2f6b3804247c581cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690913"
---
# <a name="icordebugreferencevaluesetvalue-method"></a>ICorDebugReferenceValue::SetValue メソッド

指定されたメモリアドレスを設定します。 つまり、このメソッドは、オブジェクトを指すようにこの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `value`  
 から `CORDB_ADDRESS` このが指すオブジェクトのアドレスを示す値です `ICorDebugReferenceValue` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
