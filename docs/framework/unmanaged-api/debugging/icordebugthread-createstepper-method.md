---
title: ICorDebugThread::CreateStepper メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
ms.openlocfilehash: dcaa5adc41a9e451b123b088dd900f01d9161689
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688277"
---
# <a name="icordebugthreadcreatestepper-method"></a>ICorDebugThread::CreateStepper メソッド

この ICorDebugStepper スレッドのアクティブなフレームをステップ実行できるようにする、オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppStepper`  
 入出力 `ICorDebugStepper` このスレッドのアクティブフレームのステップ実行を可能にするオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 アクティブなフレームはアンマネージコードである場合があります。  
  
 `ICorDebugStepper`実際のステップ実行には、インターフェイスを使用する必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
