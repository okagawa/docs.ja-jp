---
description: '詳細については、次のページを参照してください: いい Process:: ClearCurrentException メソッド'
title: ICorDebugProcess::ClearCurrentException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: 6f356078d8d303acb39cbaa500b7592185ad55ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754031"
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException メソッド

指定されたスレッドで現在のアンマネージ例外をクリアします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a>パラメーター  

 `threadID`  
 から現在のアンマネージ例外がクリアされるスレッドの ID。  
  
## <a name="remarks"></a>解説  

 スレッドがアンマネージ例外を報告し [たときに](icordebugcontroller-continue-method.md) 、デバッグ対象では無視する必要がある場合は、このメソッドを呼び出します。 これにより、所定のスレッドで未処理の帯域内 (IB) イベントと帯域外 (OOB) イベントの両方がクリアされます。 すべての OOB ブレークポイントと単一ステップの例外は、自動的にクリアされます。  
  
 スレッドで現在のマネージ例外をインターセプトするには、 [ICorDebugThread2:: InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) を使用します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
