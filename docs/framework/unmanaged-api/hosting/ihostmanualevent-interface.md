---
description: 詳細については、「IHostManualEvent インターフェイス」を参照してください。
title: IHostManualEvent インターフェイス
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 1c70935568b9ff4080fd5bcdc372c02d354aa06f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708155"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent インターフェイス

手動リセットイベントの表現のホストの実装を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Reset メソッド](ihostmanualevent-reset-method.md)|現在の `IHostManualEvent` インスタンスをシグナル状態以外の状態にリセットします。|  
|[Set メソッド](ihostmanualevent-set-method.md)|現在の `IHostManualEvent` インスタンスをシグナル状態に設定します。|  
|[Wait メソッド](ihostmanualevent-wait-method.md)|現在の `IHostManualEvent` インスタンスが所有されるか、指定された時間が経過するまで待機するようにします。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRSyncManager インターフェイス](iclrsyncmanager-interface.md)
- [IHostAutoEvent インターフェイス](ihostautoevent-interface.md)
- [IHostSemaphore インターフェイス](ihostsemaphore-interface.md)
- [IHostSyncManager インターフェイス](ihostsyncmanager-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
