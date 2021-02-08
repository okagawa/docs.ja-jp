---
description: '詳細については、次の情報を参照してください: いい Process:: Geb Perthreadid メソッド'
title: ICorDebugProcess::GetHelperThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: ee7bd2106a37c5c67df48a54ff9ab7fa49a03f80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801021"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID メソッド

デバッガーの内部ヘルパースレッドのオペレーティングシステム (OS) スレッド ID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pThreadID`  
 入出力デバッガーの内部ヘルパースレッドの OS スレッド ID へのポインター。  
  
## <a name="remarks"></a>解説  

 マネージデバッグおよびアンマネージデバッグ中は、デバッガーによって設定されたブレークポイントにヒットした場合に、指定した ID を持つスレッドが実行された状態を維持する必要があります。 デバッガーでは、このスレッドをユーザーに対して非表示にすることもできます。 まだプロセスにヘルパースレッドが存在しない場合、 `GetHelperThreadID` メソッドは * で0を返し `pThreadID` ます。  
  
 ヘルパースレッドのスレッド ID は、時間の経過と共に変更される可能性があるため、キャッシュすることはできません。 停止イベントが発生するたびにスレッド ID を再照会する必要があります。  
  
 デバッガーのヘルパースレッドのスレッド ID は、すべてのアンマネージコードに対して、すべてのアンマネージ [コールバック:: CreateThread](icordebugmanagedcallback-createthread-method.md) イベントに対して適切になります。これにより、デバッガーはヘルパースレッドのスレッド id を判断し、ユーザーに対して非表示にすることができます。 アンマネージイベント中にヘルパースレッドとして識別されたスレッド `ICorDebugManagedCallback::CreateThread` は、マネージユーザーコードを実行しません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug。 CorDebug. h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
