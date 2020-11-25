---
title: ICorDebugStepperEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
ms.openlocfilehash: b8156b858bde550bb66a8f4ac254f850058ea1a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697195"
---
# <a name="icordebugstepperenumnext-method"></a>ICorDebugStepperEnum::Next メソッド

現在の位置から開始して、指定した数の ICorDebugStepper インスタンスを列挙から取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `celt`  
 から `ICorDebugStepper` 取得するインスタンスの数。  
  
 `steppers`  
 入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugStepper` ます。  
  
 `pceltFetched`  
 入出力実際に返されたインスタンスの数へのポインター `ICorDebugStepper` 。 が1の場合、この値は null `celt` になります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
