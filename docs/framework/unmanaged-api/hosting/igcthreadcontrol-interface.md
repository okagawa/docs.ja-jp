---
title: IGCThreadControl インターフェイス
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
ms.openlocfilehash: 02facbb0ff1c0f8978d4f4f720ab370f70f07fe2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721687"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl インターフェイス

ガベージコレクションに対してブロックされるスレッドのスケジュール設定に参加するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[SuspensionEnding メソッド](igcthreadcontrol-suspensionending-method.md)|ランタイムがガベージコレクションまたはその他の中断後にスレッドを再開していることをホストに通知します。|  
|[SuspensionStarting メソッド](igcthreadcontrol-suspensionstarting-method.md)|ランタイムがガベージコレクションまたは他の中断のためにスレッドの中断を開始していることをホストに通知します。|  
|[ThreadIsBlockingForSuspension メソッド](igcthreadcontrol-threadisblockingforsuspension-method.md)|呼び出しを行っているスレッドがブロックしようとしていることをホストに通知します。ガベージコレクションやその他の中断が考えられます。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](hosting-interfaces.md)
