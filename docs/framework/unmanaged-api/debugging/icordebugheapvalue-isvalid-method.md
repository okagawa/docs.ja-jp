---
description: '詳細については、次の情報を参照してください:: の実行します。'
title: ICorDebugHeapValue::IsValid メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: 27eca844170b31934cd32dad5cf5fccc0b0e324e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660791"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid メソッド

この値によって表されるオブジェクトが有効かどうかを示す値を取得します。  
  
 このメソッドは .NET Framework バージョン2.0 では非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pbValid`  
 入出力ヒープ上のこの値が有効かどうかを示すブール値へのポインター。  
  
## <a name="remarks"></a>解説  

 値は、ガベージコレクターによって回収されている場合は無効です。  
  
 このメソッドの使用は非推奨とされました。 .NET Framework 2.0 では、すべての値は、"の値は無効になります。 [" が呼び出されるまで、](icordebugcontroller-continue-method.md) すべての値が有効になります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
