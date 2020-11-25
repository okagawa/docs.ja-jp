---
title: ICorDebugStepper::SetInterceptMask メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: 814bf87039ef57056f13994af1b873f8f57c7804
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718216"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask メソッド

ステップインするコードの種類を指定する値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `mask`  
 からコードの種類を指定する CorDebugIntercept 列挙子の値の組み合わせ。  
  
## <a name="remarks"></a>注釈  

 インターセプターのビットが設定されている場合、指定された種類のインターセプトコードが検出されると、ステッパが完了します。 ビットがオフの場合、インターセプトコードはスキップされます。  
  
 メソッドは、 `SetInterceptMask` [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (ユーザーの視点から見た) との予期しない相互作用を持つ場合があります。 たとえば、クラス初期化コードの表示されている (つまり、内部ではない) 部分にマッピング情報がなく、STOP_NO_MAPPING_INFO が設定されていない場合 (「 [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) メソッドと CorDebugUnmappedStop 列挙を参照してください)、ステッパはクラスの初期化をステップオーバーします。 既定では、列挙体の INTERCEPT_NONE 値のみ `CorDebugIntercept` が使用されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
