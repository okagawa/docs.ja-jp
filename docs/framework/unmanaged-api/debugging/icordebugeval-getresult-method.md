---
description: '詳細については、次を参照してください: GetResult メソッド'
title: ICorDebugEval::GetResult メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
ms.openlocfilehash: 03ab00f5c9a538e11a2046da9cbfd5ad7225231c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694241"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult メソッド

この評価の結果を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppResult`  
 入出力評価が正常に完了した場合に、この評価の結果を表す ICorDebugValue オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 `GetResult`メソッドは、評価が完了した後にのみ有効です。  
  
 評価が正常に完了した場合は、 `ppResult` 結果を指定します。 例外が発生して終了した場合は、スローされた例外が結果になります。 新しいオブジェクトの評価がの場合、結果は新しいオブジェクトへの参照になります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
