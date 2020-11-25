---
title: IDebuggerThreadControl::ThreadIsBlockingForDebugger メソッド
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
ms.openlocfilehash: 8c2741d7db60781fef12293f3be0b515a55b7885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705513"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a>IDebuggerThreadControl::ThreadIsBlockingForDebugger メソッド

このコールバックを送信しているスレッドがデバッグサービス内でブロックされようとしていることをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a>解説  

 `ThreadIsBlockingForDebugger`メソッドは常にランタイムスレッドで呼び出されます。  
  
 メソッドは、 `ThreadIsBlockingForDebugger` スレッドがブロックされている間に、ホストに別のアクションを実行する機会を与えます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.Net Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IDebuggerThreadControl インターフェイス](idebuggerthreadcontrol-interface.md)
