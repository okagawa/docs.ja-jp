---
description: 詳細については、「ereference メソッド」を参照してください:D。
title: ICorDebugReferenceValue::Dereference メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: af225f746a9c67a90a7ad73046cd03401e4ba735
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691108"
---
# <a name="icordebugreferencevaluedereference-method"></a>ICorDebugReferenceValue::Dereference メソッド

参照されているオブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppValue`  
 入出力この値のオブジェクトが指すオブジェクトを表す ICorDebugValue のアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 `ICorDebugValue`オブジェクトは、その参照がまだ無効になっていない場合にのみ有効です。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
