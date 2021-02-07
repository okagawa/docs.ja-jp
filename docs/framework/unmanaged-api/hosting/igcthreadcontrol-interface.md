---
description: '詳細情報: IGCThreadControl インターフェイス'
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
ms.openlocfilehash: 07c76848668b1525f4ff45ba5de746beefe0e004
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709283"
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
