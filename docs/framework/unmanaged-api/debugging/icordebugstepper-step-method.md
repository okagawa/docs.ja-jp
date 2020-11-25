---
title: ICorDebugStepper::Step メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
ms.openlocfilehash: 234705e4495a1a582f3801ad1e645f923cd6f4b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727693"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step メソッド

この ICorDebugStepper は、含まれるスレッドを1ステップずつ実行します。また、必要に応じて、スレッド内で呼び出される関数を使用したシングルステップ実行を継続します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `bStepIn`  
 から `true` スレッド内で呼び出される関数にステップインするには、をに設定します。 関数を `false` ステップオーバーするには、をに設定します。  
  
## <a name="remarks"></a>注釈  

 共通言語ランタイムがこのステッパのフレームで次のマネージ命令を実行すると、手順が完了します。 `Step`マネージコードに含まれていないステッパでが呼び出された場合、次のマネージコード命令がスレッドによって実行されると、手順が完了します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
