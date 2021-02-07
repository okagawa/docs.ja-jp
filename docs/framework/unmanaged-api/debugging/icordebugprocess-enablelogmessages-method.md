---
description: '詳細については、次のページを参照してください: いい Process:: EnableLogMessages メソッド'
title: ICorDebugProcess::EnableLogMessages メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
ms.openlocfilehash: d44f1a14611493372c7321feaa14329d5d77b01b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753992"
---
# <a name="icordebugprocessenablelogmessages-method"></a>ICorDebugProcess::EnableLogMessages メソッド

デバッガーへのログメッセージの転送を有効または無効にします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a>パラメーター  

 `fOnOff`  
 [入力] `true` ログメッセージの転送を有効にします。 `false` 転送を無効にします。  
  
## <a name="remarks"></a>解説  

 このメソッドは、によって実行される場合にのみ有効です: [: CreateProcess managedcallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) コールバックが発生します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
