---
description: '詳細について: ICorDebugStepper:: IsActive メソッド'
title: ICorDebugStepper::IsActive メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: 7ef937ac3c1e6f3ad9ad83b5fa84382cac3ac9c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803569"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive メソッド

この ICorDebugStepper が現在ステップを実行しているかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pbActive`  
 入出力 `true` ステッパが現在ステップを実行している場合はを返します。それ以外の場合はを返し `false` ます。  
  
## <a name="remarks"></a>解説  

 すべてのステップアクションは、デバッガーが完了していない場合は、次のように [実行](icordebugmanagedcallback-stepcomplete-method.md) されます。この呼び出しは、ステッパを自動的に非アクティブ化します。 [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md)を呼び出してコールバック条件に到達する前に、ステッパを途中で非アクティブにすることもできます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
