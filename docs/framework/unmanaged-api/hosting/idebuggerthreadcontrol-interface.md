---
description: '詳細情報: Iデバッガ Threadcontrol インターフェイス'
title: IDebuggerThreadControl インターフェイス
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
ms.openlocfilehash: 293a120d44b9b04d7e367546c477fb273f535310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709770"
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl インターフェイス

デバッグサービスによるスレッドのブロックおよびブロック解除についてホストに通知するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger メソッド](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|このコールバックを送信しているスレッドがデバッグサービス内でブロックされようとしていることをホストに通知します。|  
|[ReleaseAllRuntimeThreads メソッド](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|デバッグサービスがブロックされているすべてのスレッドを解放しようとしていることをホストに通知します。|  
|[StartBlockingForDebugger メソッド](idebuggerthreadcontrol-startblockingfordebugger-method.md)|デバッグサービスがすべてのスレッドのブロックを開始しようとしていることをホストに通知します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](hosting-interfaces.md)
