---
description: 詳細については、「IHostCrst インターフェイス」を参照してください。
title: IHostCrst インターフェイス
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: 7945f0087667c1d610a1a2370528b055af74d579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708880"
---
# <a name="ihostcrst-interface"></a>IHostCrst インターフェイス

スレッド処理のためのクリティカルセクションのホストの表現として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Enter メソッド](ihostcrst-enter-method.md)|クリティカルセクションに入ります。|  
|[Leave メソッド](ihostcrst-leave-method.md)|クリティカルセクションを残します。|  
|[SetSpinCount メソッド](ihostcrst-setspincount-method.md)|クリティカルセクションのスピンカウントを設定します。|  
|[TryEnter メソッド](ihostcrst-tryenter-method.md)|クリティカルセクションへの入力を試行し、成功または失敗を直ちに報告します。|  
  
## <a name="remarks"></a>解説  

 `IHostCrst` またはなどの Win32 関数を使用するのではなく、共通言語ランタイム (CLR) が、クリティカルセクションのホストの表現と直接通信できるようにし `EnterCriticalSection` `LeaveCriticalSection` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRSyncManager インターフェイス](iclrsyncmanager-interface.md)
- [IHostSyncManager インターフェイス](ihostsyncmanager-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
