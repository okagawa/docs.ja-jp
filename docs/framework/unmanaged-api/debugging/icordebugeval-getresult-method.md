---
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
ms.openlocfilehash: 86c017f581c7b980b8b0cb8bd7bdc1b0aa439afe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705825"
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
  
## <a name="remarks"></a>注釈  

 `GetResult`メソッドは、評価が完了した後にのみ有効です。  
  
 評価が正常に完了した場合は、 `ppResult` 結果を指定します。 例外が発生して終了した場合は、スローされた例外が結果になります。 新しいオブジェクトの評価がの場合、結果は新しいオブジェクトへの参照になります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
