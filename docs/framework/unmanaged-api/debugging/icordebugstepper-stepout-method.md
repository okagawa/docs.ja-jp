---
description: '詳細について: ICorDebugStepper:: StepOut メソッド'
title: ICorDebugStepper::StepOut メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: ef404c928ab711aef8032655a02cbd917416e806
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717616"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut メソッド

この ICorDebugStepper は、それを含むスレッドを1ステップずつ実行し、現在のフレームが呼び出し元のフレームに制御を返すときに完了します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>解説  

 操作は、 `StepOut` 通常は現在のフレームから呼び出し元のフレームに戻り、正常に完了します。  
  
 `StepOut`アンマネージコードでが呼び出されたときにが呼び出された場合、現在のフレームがそれを呼び出したマネージコードに戻ると、手順が完了します。  
  
 .NET Framework バージョン2.0 では、 `StepOut` STOP_UNMANAGED フラグが設定されていないため、を使用しないでください。 (ステップ実行のフラグを設定するには、 [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) を使用します。)相互運用デバッガーは、ネイティブコード自体にステップアウトする必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
