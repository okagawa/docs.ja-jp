---
description: '詳細について: ICorDebugModule2:: SetJITCompilerFlags メソッド'
title: ICorDebugModule2::SetJITCompilerFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: 72139c2fefc0eab7e76e38d07558e4386b47bc34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801064"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags メソッド

この ICorDebugModule2 の just-in-time (JIT) コンパイルを制御するフラグを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwFlags`  
 から [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列挙値のビットごとの組み合わせ。  
  
## <a name="remarks"></a>解説  

 `dwFlags`値が無効な場合、 `SetJITCompilerFlags` メソッドは失敗します。  
  
 `SetJITCompilerFlags`メソッドを呼び出すことができるのは、このモジュールの " [LoadModule](icordebugmanagedcallback-loadmodule-method.md) " コールバックの中からだけです。 コールバックが配信された後に呼び出しを試みると `ICorDebugManagedCallback::LoadModule` 失敗します。  
  
 64ビットまたは Win9x プラットフォームでは、エディットコンティニュはサポートされていません。 したがって、 `SetJITCompilerFlags` で CORDEBUG_JIT_ENABLE_ENC フラグを設定して、これらの2つのプラットフォームのいずれかでメソッドを呼び出すと、 `dwFlags` `SetJITCompilerFlags` メソッドと、 [ICorDebugModule2:: Applychanges](icordebugmodule2-applychanges-method.md)などのエディットコンティニュに固有のすべてのメソッドが失敗します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
