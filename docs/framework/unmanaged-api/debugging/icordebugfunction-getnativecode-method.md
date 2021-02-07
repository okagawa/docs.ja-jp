---
description: '詳細については、次の情報を参照してください: の関数:: GetNativeCode メソッド'
title: ICorDebugFunction::GetNativeCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 8938e11a5fdc3aa693faf04eec639941475d95ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692447"
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode メソッド

このコード例で表される関数のネイティブコードを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppCode`  
 入出力この関数のネイティブコードを表す、のコードインスタンスへのポインター。この関数が just-in-time (JIT) コンパイルされていない Microsoft 中間言語 (MSIL) コードの場合は null。  
  
## <a name="remarks"></a>解説  

 このインスタンスで表される関数が、 `ICorDebugFunction` ジェネリック型の場合と同じように JIT コンパイルされた場合、は、 `GetNativeCode` ランダムなネイティブコードオブジェクトを返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
