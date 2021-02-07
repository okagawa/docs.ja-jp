---
description: '詳細については、次を参照してください: を参照してください。値:: IsNull メソッド'
title: ICorDebugReferenceValue::IsNull メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: 9fffc869e20d1d3aa3a347ff2e026e6b55e6bd4f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691030"
---
# <a name="icordebugreferencevalueisnull-method"></a>ICorDebugReferenceValue::IsNull メソッド

この値が null 値であるかどうかを示す値を取得します。この場合、は `ICorDebugReferenceValue` オブジェクトを指していません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pbNull`  
 入出力このオブジェクトが null の場合はとなるブール値へのポインター。 `true` `ICorDebugReferenceValue` それ以外の場合は `pbNull` `false` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
