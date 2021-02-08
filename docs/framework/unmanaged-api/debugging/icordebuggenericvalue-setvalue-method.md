---
description: 詳細については、次を参照
title: ICorDebugGenericValue::SetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
ms.openlocfilehash: e284d9987c8428fadedde0024fd3c65a0d8fe7a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791479"
---
# <a name="icordebuggenericvaluesetvalue-method"></a>ICorDebugGenericValue::SetValue メソッド

指定したバッファーから新しい値をコピーします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pFrom`  
 から値のコピー元のバッファーへのポインター。  
  
## <a name="remarks"></a>解説  

 参照型の場合、値は参照であり、コンテンツではありません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
