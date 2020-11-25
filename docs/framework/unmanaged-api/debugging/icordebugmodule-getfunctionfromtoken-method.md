---
title: ICorDebugModule::GetFunctionFromToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: bf2acd897c9c45e445b864f85550ed7ed6e00886
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710156"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a>ICorDebugModule::GetFunctionFromToken メソッド

メタデータトークンによって指定された関数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `methodDef`  
 から `mdMethodDef` 関数のメタデータを参照するメタデータトークン。  
  
 `ppFunction`  
 入出力関数を表す、のオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 渡された `GetFunctionFromToken` 値 `methodDef` が Microsoft 中間言語 (MSIL) メソッドを参照していない場合、メソッドは CORDBG_E_FUNCTION_NOT_IL HRESULT を返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
