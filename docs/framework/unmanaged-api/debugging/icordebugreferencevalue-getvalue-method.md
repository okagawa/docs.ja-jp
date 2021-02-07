---
description: '詳細については、次を参照してください: を参照してください。値:: GetValue メソッド'
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
ms.openlocfilehash: 29e0c4997d3349b642381dcf69063de21c3f9330
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691022"
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
