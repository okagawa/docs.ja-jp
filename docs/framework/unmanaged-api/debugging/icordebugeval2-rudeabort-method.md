---
description: '詳細について: ICorDebugEval2:: による Deabort メソッド'
title: ICorDebugEval2::RudeAbort メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
ms.openlocfilehash: 2835fd635da007b5ee3f0e642b77f3954945f168
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693513"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort メソッド

このが現在実行している計算を中止し `ICorDebugEval2` ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>解説  

 `RudeAbort` は、エバリュエーターによって保持されているロックを解放しないため、デバッグセッションは安全ではない状態のままになります。 このメソッドは細心の注意を払って呼び出してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
