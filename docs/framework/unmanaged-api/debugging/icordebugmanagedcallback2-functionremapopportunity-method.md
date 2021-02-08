---
description: '詳細について: ICorDebugManagedCallback2:: FunctionRemapOpportunity メソッド'
title: ICorDebugManagedCallback2::FunctionRemapOpportunity メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
ms.openlocfilehash: 901a9432ddf17efabd96153581b816f653ff501d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790868"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity メソッド

コードの実行が、編集された関数の古いバージョンのシーケンスポイントに達したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pAppDomain`  
 から編集された関数を含むアプリケーションドメインを表す、のオブジェクトへのポインター。  
  
 `pThread`  
 からリマップブレークポイントが検出されたスレッドを表す、スレッドオブジェクトへのポインター。  
  
 `pOldFunction`  
 からスレッドで現在実行されている関数のバージョンを表す、のオブジェクトへのポインター。  
  
 `pNewFunction`  
 から関数の最新バージョンを表す、の関数オブジェクトへのポインター。  
  
 `oldILOffset`  
 から以前のバージョンの関数の命令ポインターの MSIL (Microsoft 中間言語) オフセット。  
  
## <a name="remarks"></a>解説  

 このコールバックでは、 [ICorDebugILFrame2:: RemapFunction](icordebugilframe2-remapfunction-method.md) メソッドを呼び出すことによって、指定された関数の新しいバージョンの適切な場所に命令ポインターを再マップする機会がデバッガーに与えられます。 場合、デバッガーは、 `RemapFunction` 次のシーケンスポイント[](icordebugcontroller-continue-method.md)では、前のコードを実行してから別のコールバックを起動して、このメソッドを呼び出すことができません。 `FunctionRemapOpportunity`  
  
 このコールバックは、指定された関数の古いバージョンを実行しているすべてのフレームに対して、デバッガーが S_OK を返すまで呼び出されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback2 インターフェイス](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
